# PLEASE ALWAYS REFER TO OFFICIAL DOCS

https://docs.voidlinux.org/

## specification

current spare

```
Model : Lenovo ThinkCentre M720q (10T7S0VH00)
CPU : Intel(R) Core(TM) i7-8700T (12) @ 4.00 GHz
GPU : Intel UHD Graphics 630 @ 1.20 GHz [Integrated]
RAM : 16G + 8G
STORAGE : 120G NVMe
```

### network

```bash
sudo xbps-install -S dbus NetworkManager
sudo rm -f /var/service/dhcpcd
sudo rm -f /var/service/wpa_supplicant
sudo rm -f /var/service/wicd
sudo ln -s /etc/sv/dbus /var/service/
sudo ln -s /etc/sv/NetworkManager /var/service/
```

### graphic (intel)

```bash
sudo xbps-install -S linux-firmware-intel mesa-dri vulkan-loader mesa-vulkan-intel intel-video-accel
```

### desktop environment (kde-plasma)

```bash
sudo xbps-install -S kde-plasma elogind sddm kde-baseapps
sudo ln -s /etc/sv/dbus /var/service/
sudo ln -s /etc/sv/elogind /var/service/
sudo ln -s /etc/sv/sddm /var/service/
```

optional (font)

```bash
sudo xbps-install -S noto-fonts-ttf noto-fonts-cjk
```

### multimedia (pipewire)

```bash
sudo rm -f /var/service/pulseaudio
sudo xbps-remove pulseaudio
sudo xbps-install -S pipewire wireplumber pipewire-pulse
sudo mkdir -p /etc/pipewire/pipewire.conf.d
sudo ln -s /usr/share/examples/wireplumber/10-wireplumber.conf /etc/pipewire/pipewire.conf.d/
sudo mkdir -p /etc/pipewire/pipewire.conf.d
sudo ln -s /usr/share/examples/pipewire/20-pipewire-pulse.conf /etc/pipewire/pipewire.conf.d/
sudo ln -s /usr/share/applications/pipewire.desktop /etc/xdg/autostart/
```
