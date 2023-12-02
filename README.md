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

A simple Github Action for configuring [ghvmctl](https://github.com/snapcrafters/ghvmctl) for use
on Github Actions runners is also available in the [snapcrafters/ci] repository, which will do the
following:

- Enable KVM on the runner
- Install and initialise LXD
- Install and configure `ghvmctl`

The Github Action can be used like so:

```yaml
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Setup ghvmctl
        uses: snapcrafters/ci/setup-ghvmctl@main
```

[snapcrafters/ci]: https://github.com/snapcrafters/ci/main/setup-ghvmctl
