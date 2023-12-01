<h1 align="center">ghvmctl</h1>

<p align="center"><b>This is the snap for `ghvmctl`</b>, <i>“Easily create and manage desktop VMs for testing snap packages in CI.”</i>.

<p align="center"><a href="https://snapcraft.io/ghvmctl"><img src="https://snapcraft.io/ghvmctl/badge.svg" alt="ghvmctl badge"/></a></p>

<p align="center">Published for <img src="https://raw.githubusercontent.com/anythingcodes/slack-emoji-for-techies/gh-pages/emoji/tux.png" align="top" width="24" /> with 💝 by Snapcrafters</p>

## About

A utility for creating and manipulating desktop virtual machines using LXD, primarily for
installing and running desktop applications in CI pipelines so that screenshots can be gathered
automatically as part of the QA process.

## Install

    sudo snap install ghvmctl
    sudo snap connect ghvmctl:lxd lxd:lxd

[![Get it from the Snap Store](https://snapcraft.io/static/images/badges/en/snap-store-black.svg)](https://snapcraft.io/ghvmctl)

([Don't have snapd installed?](https://snapcraft.io/docs/core/install))
