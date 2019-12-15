# gratis

Fork from [Percheron-Electronics][perch].

This repo contains [a fix][pr] for [this issue][issue] that occurs
when running the original repo on the Raspberry Pi kernel 4.9+.

Alternatively, one can downgrade the kernel:

```
sudo rpi-update 52241088c1da59a359110d39c1875cda56496764
```


## Build instructions

Requirements

```
sudo apt-get -y install  libi2c-dev i2c-tools python-smbus libfuse-dev python-imaging
```

Build

```
git clone https://github.com/Percheron-Electronics/gratis
cd gratis/PlatformWithOS
make rpi
sudo make rpi-install
```

Then reboot.


## Usage

Start the fuse driver:

```
sudo systemctl start epd-fuse
```

Now test the display. The following command should clear the display:

```
sudo echo C >> /dev/epd/command
```

And this should show a series of test images:

```
cd PlatformWithOS/driver-common/
sudo ./epd_test_screen 2.7
```


[perch]: https://github.com/Percheron-Electronics/gratis
[issue]: https://github.com/repaper/gratis/issues/62
[pr]: https://github.com/repaper/gratis/pull/64

---

Gratis is a Repaper.org repository, initiated by E Ink and PDI for the purpose of making sure ePaper can go everywhere.
