---
description: A guide to build up your installer from scratch.
---

# Quick Start

LiftInstall is designed to be tweakable from the ground up, but the defaults should work regardless for most projects. This guide will bring you through setting up a basic version of the installer.

LiftInstall should, out of the box, support Windows, OS X, and Linux (x64, x86). Other platforms may be supported as well (such as ARM), though these have not gone through the same level of testing.

## Getting Started

There are a few files that are configurable right out of the gate:

* The "bootstrap" configuration. This is shipped directly in your binary, and contains the name of your project, as well as a URL to:
* The main configuration. This is the bulk of the magic. Here you specifiy different kinds of packages that your installer can provide.
* The icon and logo for your application.

The following guide will step you through making these.

In order to get a initial version of LiftInstall running, you are going to need a few things:

* Somewhere to place your application binaries. This can be GitHub's Releases sections, Amazon S3, or whereever else you can store application binaries.
* Somewhere to store your main configuration file, which is downloaded dynamically. This is just downloaded over HTTP, so this can be a GitHub repo or anything really.
*   Dependencies for building LiftInstall:

    *   For all platforms, `cargo` should be available on your PATH. [Rustup](https://rustup.rs/) is the&#x20;

        recommended way to achieve this. Stable or Nightly Rust works fine.
    * For Windows (MSVC), you need Visual Studio installed.
    * For Windows (Mingw), you need `gcc`/`g++` available on the PATH.
    * For Mac, you need Xcode installed, and Clang/etc available on the PATH.
    * For Linux, you need `gcc`/`g++`, `webkit2gtk`, and `libssl`. For Ubuntu 18.04 this would look like:

    ```
    # apt install -y build-essential libwebkit2gtk-4.0-dev libssl-dev
    ```

If you want to verify that you have the latest Rust toolchain installed, you can use the following:

```bash
$ rustup update
```

Firstly, you are going to want to download a copy of the [source code](https://github.com/j-selby/liftinstall) for the project using the following:

```bash
$ git clone https://github.com/j-selby/liftinstall.git
```

Once you have completed these steps, you are ready to move on to [getting your config ready](writing-your-configuration-file.md).
