# The Problem
Anydesk doesn't work on the newer Raspberry Pi OS Bookworm.

## Workaround
Until Anydesk releases a version of the software that is compatible with Debian Bookworm, Anydesk cannot be used.
Anydesk is still usable ONLY IN THE 32 BITS version. So, in order for this to work, you have to have the 32-bit build.

Download the official Anydesk build from: [https://anydesk.com/en/downloads/raspberry-pi](https://anydesk.com/en/downloads/raspberry-pi)

Download the libraries (files ending in .so from this repo and copy them to `/usr/lib`. DO NOT OVERWRITE.


Use raspi-config:


```bash
sudo raspi-config
```

Select the advanced options (Number 6) and select option A6 (Wayland) and then W1 (X11), select <OK>, press enter and then reboot.

Use apt to install the missing library, so Anydesk installs from the regular package:

```bash
sudo apt install libegl1-mesa-dev
```

Anydesk will not show the regular window. Instead, you have to use the CLI to bring up the appropriate windows:

```bash
sudo anydesk --admin-settings
anydesk --show-id
```

This should get anydesk functional, so you can remote your Pi.
