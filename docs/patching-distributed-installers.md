# Patching Distributed Installers

Once you distribute your installer, you may think you are done. However, if a change to the installer binary itself needs to occur, there _is_ a mechanism to do this.

Firstly, build your new binary, pointing to a new main configuration file, and place it somewhere accessible via HTTP.

Make sure this binary points to a **new** main configuration file, else you are going to cause a infinite self-update loop!

Secondly, add the following to the top of your main configuration file, preserving current contents:

```javascript
new_tool = "url to installer"
[...]
```

When the installer is launched it will be swapped out with this new binary and continue whatever it was doing.
