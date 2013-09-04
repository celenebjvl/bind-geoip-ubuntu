This repository contains ready-to-build packages for bind 9.8.5-P2

To checkout,

```bash
git clone https://github.com/celenebjvl/bind-geoip-ubuntu.git -b 9.8.5-P2
cd bind-geoip-ubuntu
mv debian ../
cd ../
mv bind-geoip-ubuntu bind-9.8.5-P2
tar czf bind9_9.8.5.P2.orig.tar.gz bind-9.8.5-P2
mv debian bind-9.8.5-P2/debian
cd bind-9.8.5-P2

```
You are now ready to build bind9 with the bind-geoip patch!
Make sure you update the info in debian/changelog with your own.

You can build source packages for uploading to Launchpad by running the below in the source directory.

```bash
debuild -S
```
