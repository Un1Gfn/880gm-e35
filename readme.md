[manual](https://www.msi.com/Motherboard/support/880GME35#down-manual)

|Key|Function|
|<kbd>DEL</kbd>|BIOS Setup|
|<kbd>F11</kbd>|Select Boot Device|

[Hiren's BootCD](https://www.hirensbootcd.org/download/)

```bash
su -
woeusb -v --device /home/darren/880GM-E35/HBCD_PE_x64.iso /dev/<TYPE_MANUALLY>
```

https://wiki.archlinux.org/index.php/Installation_guide

```bash
pacstrap \
  /mnt \
  base linux linux-firmware \
  man-db man-pages \
  neovim nano \
  iproute2 net-tools ethtool dhcpcd 

grub-install -v --target=i386-pc /dev/<TYPE_MANUALLY>
```

```
  Fontconfig configuration is done via /etc/fonts/conf.avail and conf.d.
  Read /etc/fonts/conf.d/README for more information.

  Configuration via /etc/fonts/local.conf is still possible,
  but is no longer recommended for options available in conf.avail.

  Main systemwide configuration should be done by symlinks
  (especially for autohinting, sub-pixel and lcdfilter):

  cd /etc/fonts/conf.d
  ln -s ../conf.avail/XX-foo.conf

  Check also https://wiki.archlinux.org/index.php/Font_Configuration
  and https://wiki.archlinux.org/index.php/Fonts.
```

```bash
groupadd sudo
useradd -m -G sudo,video -s /bin/bash darren
```

```bash
sshfs darren@192.168.1.104:/home/darren /home/darren/880GM-E35/mnt
fusermount3 -u /home/darren/880GM-E35/mnt
```

```bash
DISPLAY=:0.0 xrandr --output VGA-1 --off
DISPLAY=:0.0 xrandr --output HDMI-1 --off
```

bash reads /home/darren/.bashrc for darren but ignores /root/.bashrc and only takes /root/.bash_profile

Login w/o Ctrl-Alt
```bash
systemctl enable getty@tty2.service
```
