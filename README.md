# Lamponcino

A proper README will come, for the moment some fragmented information below.

## Prepare Raspberry Pi

- Download the Raspberry Imager and install the **desktop** version
<https://www.raspberrypi.org/downloads/>

- Enable SSH ([guide](https://www.raspberrypi.org/documentation/remote-access/ssh/))

```bash
touch /Volumes/boot/ssh
```

- Configure WiFi

- <https://www.raspberrypi.org/documentation/configuration/wireless/headless.md>
- <https://learn.adafruit.com/adafruits-raspberry-pi-lesson-3-network-setup/setting-up-wifi-with-occidentalis>

```bash
vim /Volumes/boot/vim wpa_supplicant.conf
```

And copy the following configuration inside, remember to update the values:

```text
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=De

network={
 ssid="<SSID>"
 psk="<PASSWORD>"
 scan_ssid=1
}
```

- Boot up your Pi

- add ssh key

```bash
ssh pi@raspberrypi.local
```

```bash
ssh-copy-id pi@raspberrypi.local
```

Or if you wanna use a custom key:

1. copy the key in the `~/.ssh/authorized_keys`

```bash
cat ~/.ssh/id_raspi_rsa.pub | ssh pi@raspberrypi.local 'mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys'
```

2. Add the new key locally to the agent

```bash
ssh-add ~/.ssh/id_raspi_rsa
```

- Stop the mechanical voice by following the welcome message

https://raspberrypi.stackexchange.com/questions/118911/how-do-i-stop-the-audio-message-to-install-the-screen-reader-press-control-alt

- Apparently, with the latest Buster version the waveshare is properly setup.

- Enabling VNC:
  - follow the instruction: https://www.raspberrypi.org/documentation/remote-access/vnc/

- Potentially change host name [link](https://www.howtogeek.com/167195/how-to-change-your-raspberry-pi-or-other-linux-devices-hostname/)


- Find your IP [link](https://www.raspberrypi.org/documentation/remote-access/ip-address.md)

# Autologin

It should be the default, otherwise enable it manually
