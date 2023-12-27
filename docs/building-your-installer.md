# Building your Installer

At this point, you should have several things done:

* You have your [main configuration file(s)](writing-your-configuration-file.md) written.
* You have your ["bootstrap" configuration file(s)](writing-your-bootstrap-configuration-file.md) written.

You are going to want a pretty icon for your application. This can be placed as a `.ico` file at `static/favicon.ico`. Further, place your applications logo as a `.png` file at `static/logo.png`.

## Building

Whenever you make changes, you should be rebuilding your binary. There is no special process here - we just use Cargo, the Rust packaging solution.

When you are ready, type the following:

```bash
$ cargo build
```

After this operation completes (it will be slow the first time), you should have an application binary  stored in `target/debug/liftinstall[.exe]`. Test this out, and see how it runs (on Windows, a command line window will be spawned for debug builds). If needed, go back and modify your application, and come back.

Both debugging and release installers generate log files at `installer.log` in their directory. If stuff breaks, take a look there!

Whenever you are ready to release to the world, type the following:

```bash
$ cargo build --release
```

This will produce a optimised binary which will be placed at `target/release/liftinstall[.exe]`. Upload this to your hosting service of choice, or distribute it otherwise, and you are ready to go! You may want to sign this binary using platform-specific tools if you want.
