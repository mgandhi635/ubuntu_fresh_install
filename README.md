# ubuntu_fresh_install
Instructions and scripts for a fresh Ubuntu or Pop! OS install.

## Adding Windows Boot Manager to systemd boot menu

In short, the method to do this is to mount the boot partition of windows (this can be found by running `lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT`). Typical Windows installs will have a 100 MB partition. Then this partition can be copied to the boot partition of the Pop! Os install.

```
sudo mkdir /mnt/tmp
mount /dev/nvme0n1p1 /mnt/tmp
cp -r -/mnt/tmp/EFI/Microsoft /boot/efi/EFI
```

Note this only works for UEFI installs. You can `ls` the `/mnt/tmp` directory to make sure that the `EFI/Microsoft` folder is in there. Finally, make sure that the default boot device is the partition with Pop! OS installed.


## Nvidia Drivers

A Pop! OS install will usually come with the proprietary nvidia drivers installed. The package manager can handle the driver installation. You can test if everything is working correctly by running `nvidia-smi` in a terminal.

## Docker

Docker can be installed via a snap package by runnining `sudo snap install docker`. In order to run the docker command without sudo, you have to add your user to the docker group. 

```sudo usermod -aG docker $USER```

You must reboot in order for this to take effect.
