zoot
====

redhat 6.2

build instructions
------------------

```
grep -v '// ' zoot_annotated.json > zoot.json
packer build zoot.json
```

fix up display
--------------

After the box builds, login as root from VirtualBox console, and do
the following to fix the display:

```
perl -lpi -e 'print "    Clocks            25.2" if $_ =~ "Chipset"' /etc/X11/XF86Config
```

[Why do this?](https://forums.virtualbox.org/viewtopic.php?t=77226#p359486)

The resulting /etc/X11/XF86Config file should look like this:

```
Section "Device"
    Identifier        "Generic VGA Card"
    VendorName        "Unknown"
    BoardName         "Unknown"
    Clocks            25.2
    Chipset           "generic"
Endsection
```
