# Writing your Main Configuration File(s)

Your configuration file is where the majority of your applications' metadata is fetched from during operation. This tells the application what packages are available, what the name of the application is, and so on. This is written using TOML.

As installers for platforms each have separate "bootstrap" configuration files, these main configuration files as such can also be separate. This allows you to have platform specific shortcuts (e.g. Windows needs `.exe`), or pretty much anything else.

This is what a configuration file looks like (with descriptions afterwards!):

```javascript
installing_message = "Reminder: yuzu is an <b>experimental</b> emulator. Stuff will break!"

[[packages]]
name = "yuzu Nightly"
description = "The nightly build of yuzu contains already reviewed and tested features."
default = true
    [packages.source]
    name = "github"
    match = "^yuzu-windows-mingw-[0-9]*-[0-9a-f]*.zip$"
        [packages.source.config]
        repo = "yuzu-emu/yuzu-nightly"
    [[packages.shortcuts]]
    name = "yuzu Nightly"
    relative_path = "nightly-mingw/yuzu.exe"
    description = "Launch yuzu (Nightly version)"

[[packages]]
name = "yuzu Canary"
description = "The canary build of yuzu has additional features that are still waiting on review."
    [packages.source]
    name = "github"
    match = "^yuzu-windows-mingw-[0-9]*-[0-9a-f]*.zip$"
        [packages.source.config]
        repo = "yuzu-emu/yuzu-canary"
    [[packages.shortcuts]]
    name = "yuzu Canary"
    relative_path = "canary-mingw/yuzu.exe"
    description = "Launch yuzu (Canary version)"

```

Let's break this down:

*   "installing\_message"

    &#x20;This is a message placed in the installing screen. This could be a summary of your latest updates, general information, or it could be left empty (though you should still specify it!). This can use HTML (have fun with your `<marquee>`).
*   "\[\[packages]]"

    Each package has it's own TOML table entry.

    *   "name"

        This is the user-presented name for this package.
    *   "description"

        This is a **short** description of your package.
    *   "default" (optional)

        This sets this package to be installed by default if the user doesn't manually deselect it.
    *   "\[packages.source]"

        This starts the definition for the package "source", where packages get downloaded from.

        *   "name"

            The source name for this package. For example, "github".
        *   "match"

            Some sources can have multiple files for a particular version/release. This is a regex pattern applied to files found. The first file matching this regex pattern will be downloaded.
        *   "\[packages.source.config]"

            Most sources are going to need additional metadata about, for example, the repo in which they can be found.

            *   "repo" (for "github" source)

                This is a reference to a GitHub repo containing your releases for this package. This is formatted as "username/repo".
    *   "\[\[package.shortcuts]]"

        This is a table entry (i.e you can specify this more than once) of shortcuts for the current package. Shortcuts are directed through the updater before launching your main executable.

        *   "name"

            The name of this shortcut. Keep this sane as this will be used as the filename on Windows.
        *   "relative\_path"

            The path to an executable for this shortcut. This is calculated relatively to the install directory.
        *   "description"

            Description used for this shortcut. This is generally stored in the file's metadata.

##

Take your time to work out what your main configuration should look like, and publish it to a HTTP server somewhere. Remember you can have multiple configuration files for multiple platforms, which is recommended. Next, move onto [building the "bootstrap" configuration file](writing-your-bootstrap-configuration-file.md).

