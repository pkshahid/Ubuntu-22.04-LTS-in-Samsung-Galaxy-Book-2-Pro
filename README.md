# Ubuntu-22.04-LTS-in-Samsung-Galaxy-Book-2-Pro
Solutions for the issues occurred after installation of Ubuntu 22.04 LTS in Samsung Galaxy Book 2 Pro

# Overview
1. Display Brightness Control not working.
2. Built-in Speaker not working.
3. Wifi Not Working.

# 1. Display Brightness Control not working.
Solution : 
1. Open `grub` file in any editor.<br>
   ` sudo nano /etc/default/grub `
2. Update `GRUB_CMDLINE_LINUX_DEFAULT` value by adding `i915.enable_dpcd_backlight=3` to existing value.
   So that, the final result should be `GRUB_CMDLINE_LINUX_DEFAULT="quiet_splash i915.enable_dpcd_backlight=3"`.
   <br><br>
   ![screenshot](https://github.com/pkshahid/Ubuntu-22.04-LTS-in-Samsung-Galaxy-Book-2-Pro/blob/main/brightness.png?raw=true)
4. Save and Reboot the system or run `update-grub`.

# 2. Built-in Speaker not working.
Solution : 
1. Update Kernal to `6.4.6`.
   - Check currently installed version.<br>
      ` uname -r `
   - Download the mainline Linux kernel of version `v6.4.6` from [here](https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N%3BO%3DD&ref=itsfoss.com) <br>
   <br><br>
   ![screenshot](https://github.com/pkshahid/Ubuntu-22.04-LTS-in-Samsung-Galaxy-Book-2-Pro/blob/main/kernal.png?raw=true)
<br><br>
        - ` wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.4.6/amd64/linux-headers-6.4.6-060406-generic_6.4.6-060406.202307241739_amd64.deb `
        - ` wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.4.6/amd64/linux-headers-6.4.6-060406_6.4.6-060406.202307241739_all.deb `
        - ` wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.4.6/amd64/linux-image-unsigned-6.4.6-060406-generic_6.4.6-060406.202307241739_amd64.deb `
        - ` wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.4.6/amd64/linux-modules-6.4.6-060406-generic_6.4.6-060406.202307241739_amd64.deb `
   - Install the downloaded kernel
        - ` sudo dpkg -i *.deb `
   - Reboot Ubuntu , disable `Secure Boot` in UEFI Settings , save and restart

# 3. Wifi Not Working.
Solution : 
1. Open and edit `/etc/modprobe.d/iwlwifi.conf`. <br>
   ` sudo nano /etc/modprobe.d/iwlwifi.conf `
2. Add following line to the above file <br>
   `options iwlwifi 11n_disable=1 swcrypto=1`
   <br><br>
   ![screenshot](https://github.com/pkshahid/Ubuntu-22.04-LTS-in-Samsung-Galaxy-Book-2-Pro/blob/main/wifi.png?raw=true)
   <br><br>
4. Save and Reboot the system.
