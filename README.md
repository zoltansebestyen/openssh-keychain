openssh-keychain
================

OpenSSH mod to store passwords in OS X keychain. It's a patch to various versions of openssh, adding a hook to the code to store and retrieve passwords to/from OS X keychain.
This guide describes the steps to install this patch on the openssh package distributed by MacPorts, but patch should work with other (source) distributions.

Installation (brew)
=======================

Run 'brew edit homebrew/dupes/openssh' and the following to the config, at 36th line:

```
  #
  # keychain patch
  patch do
    url "https://raw.githubusercontent.com/zoltansx/openssh-keychain/master/openssh-7.6p1.patch"
    sha256 "7356089e21efcaf2602c002a836c3ba32b213e19ef6e32ed4ae583500ba8c622"
  end
```

Install from sources with

```
brew install -v --build-from-source  openssh
```

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

