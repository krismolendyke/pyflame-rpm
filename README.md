This repository holds the spec file used for Pyflame RPM packaging. This
repository is used to trigger builds for the [eklitzke/pyflame
COPR](https://copr.fedorainfracloud.org/coprs/eklitzke/pyflame/). Perhaps it
will be in Fedora one day.

# Build

Rough sketch of getting a RPM built on Amazon Linux 2017.09 from this
hacked spec file:

```sh
yum install rpmdevtools yum-utils
rpmdev-setuptree
cp pyflame.spec rpmbuild/SPECS/
yum-builddep rpmbuild/SPECS/pyflame.spec
spectool -R -g rpmbuild/SPECS/pyflame.spec
rpmbuild -bb rpmbuild/SPECS/pyflame.spec
rpm -Uvh rpmbuild/RPMS/x86_64/*.rpm
```
