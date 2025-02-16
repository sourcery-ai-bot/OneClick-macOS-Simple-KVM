---
title: One-Click Method
permalink: /oneclick/
---

## OneClick Method
- `setup.sh` is for Debian based Linux Repositories like Ubuntu
- `setupArch.sh` is for Arch based Linux Repositories like Manjaro.
- `setupFedora.sh` is for Fedora based Linux Repositories.
- `setupSUSE.sh` is for openSUSE Tumbleweed

Run `./setup.sh` or the correct one depending on your Linux OS to make the VM. Monterey may not work, as it is very picky about hardware.
Once the VM boots up, just hit enter even if it's a black screen or a cut off image (do this every boot) Then format the biggest drive as macOS Extended Journaled (should be a little bigger than 64GB, then go to reinstall macOS and install it to the newly formatted drive.

Once it boots, you can install macOS. Remember to partition in Disk Utility first! (macOS extended journaled). Once macOS is succesfully installed, you can select the macOS partition with ctrl+enter to set it as the default boot and automatically boot up the VM without the macOS Installer attached. This will prevent OpenCore from default booting the installer.

## You're done!

If the mouse is not aligned properly, edit the basic.sh file and change `-usb -device usb-kbd -device usb-tablet \` to `-usb -device usb-kbd -device usb-mouse \` or the other way around.

If you get an error that says access denied, run `sudo ./basic.sh` which will give it admin privelages. If you get an error that looks like: 
```
Requested operation is not valid: Setting different SELinux label on /opt/dir/OneClick-macOS-Simple-KVM/firmware/OVMF_VARS-1024x768.fd which is already in use
```
edit `/etc/libvirt/qemu.conf` and change/add this line `remember_owner=0`

To fine-tune the system and improve performance, look in the `docs` folder for more information on [adding memory](https://notaperson535.github.io/OneClick-macOS-Simple-KVM/docs/performance), setting up [bridged networking](https://notaperson535.github.io/OneClick-macOS-Simple-KVM/docs/networking), adding [passthrough hardware (for GPUs)](https://notaperson535.github.io/OneClick-macOS-Simple-KVM/docs/passthrough), tweaking [screen resolution](https://notaperson535.github.io/OneClick-macOS-Simple-KVM/docs/resolution), and [enabling sound features](https://notaperson535.github.io/OneClick-macOS-Simple-KVM/docs/passthrough).
