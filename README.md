<h1 align="center">ghvmctl</h1>

<p align="center"><i>"Easily create and manage desktop VMs for testing snap packages in CI"</i>

<p align="center"><a href="https://snapcraft.io/ghvmctl"><img src="https://snapcraft.io/ghvmctl/badge.svg" alt="ghvmctl badge"/></a></p>

<p align="center">Published for <img src="https://raw.githubusercontent.com/anythingcodes/slack-emoji-for-techies/gh-pages/emoji/tux.png" align="top" width="24" /> with 💝 by Snapcrafters</p>

## About

A utility for creating and manipulating desktop virtual machines using LXD, primarily for
installing and running desktop applications in CI pipelines so that screenshots can be gathered
automatically as part of the QA process.

## Install the snap

    sudo snap install ghvmctl
    sudo snap connect ghvmctl:lxd lxd:lxd

([Don't have snapd installed?](https://snapcraft.io/docs/core/install))

## Use the Github Action

A simple Github Action for configuring [ghvmctl](https://github.com/jnsgruk/ghvmctl) for use on
Github Actions runners is also included in this repository. It has three major functions:

- Enable KVM on the runner
- Install and initialise LXD
- Install and configure `ghvmctl`

The Github Action can be used like so:

```yaml
jobs:
  clever-vm-action:
    runs-on: ubuntu-latest
    steps:
      - name: Setup ghvmctl
        uses: jnsgruk/ghvmctl/setup-ghvmctl@main

      - name: Prepare test environment
        run: |
          # Prepare the VM, install and launch the app on the desktop
          ghvmctl prepare
          ghvmctl install-snap signal-desktop --channel candidate
          ghvmctl run-snap signal-desktop

      - name: Take screenshots & output logs
        run: |
          ghvmctl screenshot-full
          ghvmctl screenshot-window
          ghvmctl exec "cat /home/ubuntu/signal-desktop.log"

      - name: Upload screenshots
        uses: actions/upload-artifact@v3.1.3
        with:
          name: "screenshots"
          path: "~/ghvmctl-screenshots/*.png"
```
