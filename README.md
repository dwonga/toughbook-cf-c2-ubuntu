# Tricks for Toughbook CF-C2 and Ubuntu
In an attempt to save others time here's some tricks and hacks I've done on my Ubuntu 20.04 install on a CF-C2.

## Fix for screen birghtness not changing
Edit /etc/default/grub and change this line:  
`GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"`  
to:  
`GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="`  

## GPS Time Update
Check out the gpsd folder to see how I was able to get GPS time to work.

## Temporary fix for speaker not working on boot
1. open alsamixer
2. press F6
3. select Intel PCH
4. use right arrow to slect "Headphone"
5. use up arrow to set desired volume

# Final solution to audio (based on hestela solution, modified by dwonga)
-------------------------------------------------------------------------
add this line that enables "headphone" output (the real audio output in CF-C2)

$ amixer -c 1 set Master playback 100% unmute

We will do it by using crontab

1. crontab -e
2. add this line at first:
@reboot      amixer -c 1 set Headphone playback 100% unmute

(Thanks to hestela for their solutions)
