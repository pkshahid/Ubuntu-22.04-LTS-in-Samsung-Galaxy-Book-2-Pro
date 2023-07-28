# Ubuntu-22.04-LTS-in-Samsung-Galaxy-Book-2-Pro
Issues and solutions for the issues occurred after installation of Ubuntu 22.04 LTS in Samsung Galaxy Book 2 Pro

# Overview
1. Display Brightness Control not working.
2. Built-in Speaker not working.
3. Wifi Not Working.

# 1. Display Brightness Control not working.
Solution : 
1. Open `grub` file in any editor.
   ` sudo nano /etc/default/grub `
2. Update `GRUB_CMDLINE_LINUX_DEFAULT` value by adding `i915.enable_dpcd_backlight=3` to existing value.
   So that, the final result should be `GRUB_CMDLINE_LINUX_DEFAULT="quiet_splash i915.enable_dpcd_backlight=3"`.
   ![Screenshot](https://github.com/pkshahid/Ubuntu-22.04-LTS-in-Samsung-Galaxy-Book-2-Pro/blob/main/brightness.png?raw=true)
4. Save and Reboot the system or run `update-grub`.
