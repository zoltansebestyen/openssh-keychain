openssh-keychain
================

OpenSSH mod to store passwords in OS X keychain. It's a patch to various versions of openssh, adding a hook to the code to store and retrieve passwords to/from OS X keychain.
This guide describes the steps to install this patch on the openssh package distributed by MacPorts, but patch should work with other (source) distributions.

Installation (MacPorts)
=======================

```
# We don't install the code, just make it ready for the patch
sudo port build openssh

# Note that parts of the path may vary, but it always starts with
# "/opt/local/var/macports/build/", i.e. can figured out easily.
cd /opt/local/var/macports/build/_opt_local_var_macports_sources_rsync.macports.org_release_tarballs_ports_net_openssh/openssh/work/openssh-6.6p1

sudo bash

patch < ~/openssh-6.6p1-keychain.patch
make install
```

License
----

MIT

