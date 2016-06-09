# docker_mac_osxfs_error
Reproducing osxfs cannotwrite error

### To reproduce ###

Simply run

    docker run -it --rm -v ~/blah:/home/dev andyneff/docker_mac_osxfs_error

### Expected Error ###

It fails on one fo the `extracting debug info from` steps, towards the end of the process.

```
extracting debug info from /home/dev/rpmbuild/BUILDROOT/proj-4.9.1-2.el7.centos.x86_64/usr/bin/cs2cs
extracting debug info from /home/dev/rpmbuild/BUILDROOT/proj-4.9.1-2.el7.centos.x86_64/usr/bin/geod
extracting debug info from /home/dev/rpmbuild/BUILDROOT/proj-4.9.1-2.el7.centos.x86_64/usr/bin/nad2bin
extracting debug info from /home/dev/rpmbuild/BUILDROOT/proj-4.9.1-2.el7.centos.x86_64/usr/bin/proj
eu-strip: while writing '/home/dev/rpmbuild/BUILDROOT/proj-4.9.1-2.el7.centos.x86_64/usr/bin/proj': cannot write data to file
```

I have had it fail on cs2cs, geo, and proj, or not fail at all and actually succeed!

### Version ###

```
Client:
 Version:      1.11.1
 API version:  1.23
 Go version:   go1.5.4
 Git commit:   5604cbe
 Built:        Wed Apr 27 00:34:20 2016
 OS/Arch:      darwin/amd64

Server:
 Version:      1.11.1
 API version:  1.23
 Go version:   go1.5.4
 Git commit:   8b63c77
 Built:        Fri Jun  3 08:34:52 2016
 OS/Arch:      linux/amd64
```

Home directory is mounted as `(hfs, local, journaled)`
