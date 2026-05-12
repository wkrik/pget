# Update to a newer version.

### Automated:
  In the pget directory of the new version, run: 
```
    $ ./setup_pget
```

  It will check/validate the current and new versions.
  It may request that the existing version be "moved" out of the way.
  Once everything is validated, it updates the version.

### Manual:
  Since you already have .vimrc files configured, and 
  the symlink /usr/local/bin/pget in place, just rename 
  the current version and copy in the new version.

1. Get the current version installed:
```
    $ pget --version
```
2. Move the current version out of the way.

```
    $ sudo mv /opt/pget /opt/pget-[version]
```

3. Copy the new version (at the pget parent directory) in place:
```
    $ sudo cp -r pget/ /opt/
```

  That's it. 
