# Alternatives

LiftInstall is far from the only installer/updater framework out there, but for obvious reasons they have had various problems/issues that make them hard to wrangle with. Regardless, here are alternatives:

* WiX Toolset
  * Windows only
  * Highly integrated with that ecosystem
* QtIFW
  * Cross platform
  * Hard to modify/maintain
  * Has very hardcoded package layouts
* Native package managers (apt, dpkg, homebrew), or Flatpack/Snaps/Docker:
  * Generally, best option if targeting these operating systems individually
  * Highly integrated with that ecosystem
  * Generally is going to need more setup

