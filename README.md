This repository contains ready-to-build-packages for bind 9.8.5-P2.


Security is not guaranteed though I will try to keep it as updated as possible

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

To build source packages for uploading to Launchpad PPAs, run the below

```bash
debuild -S
```

To build binary packages to install, run the below

```bash
debuild -D
```

###Notes

####Getting The GeoIP Databases
You probably want to use geoip-database-contrib in Ubuntu to get the latest database, the geoip-database package is horribly out of date in some versions such as precise


This setup is quite accurate at province/state/country-wide, but not so much city-wide - I use this for SandyDNET, and you can see it in action at http://startping.com/ping/tracking.sandyd.me/52271f3c8c3dcfc823000003 (US is seperated into east/west coast servers)

####Fixing Apparmor
If you are using Apparmor with bind, you may find it useful to do the below edits.
```bash
nano /etc/apparmor.d/local/usr.sbin.named
```
And add the below line
```bash
/usr/share/GeoIP/** r,
```
and run the below to restart apparmor
```bash
sudo service apparmor restart
```
