Simple application to read current clocks of ATi Radeon cards (xf86-video-ati, xf86-video-amdgpu).

# xf86-video-ati and xf86-video-amdgpu driver
Install and run radeon-profile-daemon (https://github.com/marazmista/radeon-profile-daemon) for using this app as normal user. Otherwise, the app needs to be run with root privileges to change the power profiles (sometimes clocks readings too). You can create a text file containing `username ALL = NOPASSWD: /usr/bin/radeon-profile` under `/etc/sudoers.d/radeon-profile`.

Here is a tip to run the app as a normal user, **but note that this involves changing permissions to system files**: http://bit.ly/1dvQMhS

# Functionality

* Monitoring of basic GPU parameters (frequencies, voltages, usage, temperature, fan speed)
* DPM profiles and power levels
* Fan control (HD 7000+), definition of multiple custom curves or fixed speed
* Overclocking (amdgpu) (Wattman, Overdrive, PowerPlay etc)
* Per app profiles/Event definitions (i.e. change fan profile when temp above defined or set DPM to high when selected binary executed)
* Define binaries to run with set of environment variablees (i.e. GALLIUM_HUD, MESA, LIBGL etc)

# Dependencies

* Qt 5.6<= (qt5-base and qt5-charts) (qt5-defaults, libqt5charts5, libqt5charts5-dev for Ubuntu/Debian)
* libxrandr
* libdrm (for amdgpu, 2.4.79<=, more recent, the better)
* recent kernel (for amdgpu 4.12<=, more recent, the better)
* radeon card

For full functionality:
* glxinfo - info about OpenGL, mesa
* xdriinfo - driver info
* xrandr - connected displays


# Build
```
git clone https://github.com/marazmista/radeon-profile.git && cd radeon-profile/radeon-profile
qmake && make 
```
To install for all users, run this instead of `make`:
```
sudo make install
```

For Ubuntu 17.04, qt5-charts isn't available:
* Use `qtchooser -l` to list available profiles
* Use `qmake -qt=[profile from qtchooser]` to specify Qt root, or download and install Qt 5.9.1 from https://download.qt.io/archive/qt/5.9/5.9.1/
* Make a `qt5opt.conf` in `/usr/lib/x86_64-linux-gnu/qtchooser/` containing:
```
/opt/Qt5.9.1/5.9.1/gcc_64/bin
/opt/Qt5.9.1/5.9.1
```

# Installation
### Ubuntu 
Available for Ubuntu from PPA [stable](https://launchpad.net/~radeon-profile/+archive/ubuntu/stable) and [git develop](https://launchpad.net/~radeon-profile/+archive/ubuntu/radeon-profile) repository

Add in terminal commands:

* For git ppa: 
```
sudo add-apt-repository ppa:radeon-profile/radeon-profile
```
* For stable ppa: 
```
sudo add-apt-repository ppa:radeon-profile/stable
```
* Then run commands:
```
sudo apt update
sudo apt install radeon-profile
```

### Arch Linux
* AUR package: https://aur.archlinux.org/packages/radeon-profile-git/
* System daemon AUR package: https://aur.archlinux.org/packages/radeon-profile-daemon-git/

# Links
* System daemon: https://github.com/marazmista/radeon-profile-daemon
* Sort of official thread: http://phoronix.com/forums/showthread.php?83602-radeon-profile-tool-for-changing-profiles-and-monitoring-some-GPU-parameters
* Icon: http://proicons.deviantart.com/art/Graphics-Cards-Icons-H1-Pack-161178339

# Screenshot

Main screen
![Main screen](https://i.imgur.com/Z880p47.png)

[More screenshots](http://imgur.com/a/DMRr9)
