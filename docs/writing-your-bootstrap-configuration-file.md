# Writing your "Bootstrap" Configuration File(s)

You are also going to need "bootstrap" configuration files, which are shipped inside your installer binaries. These are tiny though:

```javascript
name = "yuzu"
target_url = "path to main configuration url for this platform"
```

These are placed in the root of your installer source repo as `bootstrap.[windows,linux,...].toml`. Specific platform names can be found [here](https://doc.rust-lang.org/std/env/consts/constant.OS.html).

Finally, you can move on to [building your installer](building-your-installer.md).
