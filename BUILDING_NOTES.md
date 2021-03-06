Instructions for building these binaries and set up a similar standalone repository...

First build and install SuperCollider and sc3-plugins on a RPi3 (or RPi2) following the instructions in the ScIDE section [here](http://supercollider.github.io/development/building-raspberrypi.html). One can also use an existing sc install assuming all the files are in their default directories.

* `mkdir supercolliderStandaloneRPI2 && cd supercolliderStandaloneRPI2`
* `cp /usr/local/bin/sc* .` #this should copy scide, sclang and scsynth
* `cp -r /usr/local/lib/SuperCollider/plugins .` #copies all plugins including sc3-plugins
* `mkdir -p share/system`
* `cp -r /usr/local/share/SuperCollider/* share/system` #copies help, classes, examples etc
* `mkdir -p share/system/Extensions/SystemOverwrites`
* `curl -o share/system/Extensions/SystemOverwrites/extLinuxPlatform.sc https://raw.githubusercontent.com/redFrik/supercolliderStandaloneRPI2/master/share/system/Extensions/SystemOverwrites/extLinuxPlatform.sc`
* `mkdir share/user`
* `curl -o share/user/archive.sctxar https://raw.githubusercontent.com/redFrik/supercolliderStandaloneRPI2/master/share/user/archive.sctxar`
* `curl -o sclang.yaml https://raw.githubusercontent.com/redFrik/supercolliderStandaloneRPI2/master/sclang.yaml`
* `curl -o autostart.sh https://raw.githubusercontent.com/redFrik/supercolliderStandaloneRPI2/master/autostart.sh`
* `curl -o mycode.scd https://raw.githubusercontent.com/redFrik/supercolliderStandaloneRPI2/master/mycode.scd`
* `curl -o run.sh https://raw.githubusercontent.com/redFrik/supercolliderStandaloneRPI2/master/run.sh`
* `curl -o share/system/sc_ide_32.png https://raw.githubusercontent.com/redFrik/supercolliderStandaloneRPI2/master/share/system/sc_ide_32.png`

Now this directory should contain what is needed to run ScIDE standalone (if started as in the README.md). Copy it to another machine with the same system and try.

publish
--
My own additional notes for this git repository...

* note which git commit was used in README.md
* note which raspbian image was used in README.md
* copy the files over to laptop...
  * `cd supercolliderStandaloneRPI2`
  * `scp pi@raspberrypi.local:supercolliderStandaloneRPI2/sc* .`
  * `rm -rf plugins`
  * `scp -r pi@raspberrypi.local:supercolliderStandaloneRPI2/plugins .`
  * `rm -rf share`
  * `scp -r pi@raspberrypi.local:supercolliderStandaloneRPI2/share .`
  * and possibly the yaml and desktop files as well if something changed
* git commit and sync
