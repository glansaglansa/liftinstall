# Introduction

LiftInstall is designed to be a dynamic, modifible way to create installers and updaters for your applications with minimal effort. While each platform each has mechanisms for installing software (which should be considered if you are willing to make the effort to do so), such as WiX on Windows, homebrew on OS X, and the various \*nix package managers, providing support for all of these platforms may not be suitable for smaller projects.

## Rationale

The primary pattern which LiftInstall is intended for is:

* Initial installation (binaries, shortcuts, etc)
* Maintenance of the application (updates to both self and packages, uninstallation)
* Hooking by other software (when your application is launched, do a update check)

LiftInstall is typically built as a single binary. This can be hosted using any service you like - this is a single, self contained binary. When this binary is launched on a client's computer, options are provided for what packages are desired, if shortcuts should be installed, and where the application should be placed. The application then fetches binary distributions packaged in a archive format from any number of services - GitHub, or a generic HTTP server. These archives are then extracted, a database is written, and the installer binary has a 1-to-1 copy made in the installation directory.

If a user wants to update or modify their installation afterwards, they launch this copied binary, which will detect an adjecent database file, and provide the user with options.

Finally, a command line interface can be hooked by external applications (generally, the same binaries that were downloaded previously) for scriptable modification of the installation.
