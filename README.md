# PI-shutdown-push-button
A header mounted push button that will safely shutdown the Raspberry PI

This project describes a very simple but very very usefull tool that allows you to safely shutdown your Raspberry PI. This might be particularly usefull when, for instance, your headless PI is unreacheable because your network/wifi-router happens to be down at the exact moment you need to shut down the PI ... you probably know what I mean... the question is then how to safely shutdown the PI without risking any SD card corruptions. 

Now I didn't devised this setup, the credit all goes to [GIMX](https://gimx.fr/wiki/index.php?title=RPi#Autostart_GIMX_at_boot_without_GUI) where I found it. A bit of advertisement here:... GIMX is a cool project that allows old gamers, like me, to use the mouse and keyboard to play games on the PlayStation or XBox. Sounds like a gimmick doesn't it :-) !!!

I thought this was so usefull that I wanted to replicate it here so I would not loose it. 

My meager contribution is repackaging the push button and the led to easily mount them on the PI header.

The led will turn on when a program of your choosing is running, in my case it is python...

### Breadboard view

`Fritzing` does not allow the kind of 3D drawing I need to explain how to mount the resistors and the push button (PB) on top of a dual inline 6 pins female header, sorry for the distorded "perspective" view...

![PI_header_BP_led](https://github.com/jeanrocco/PI-shutdown-push-button/blob/master/PI_Header_PB_LED_bb1.png)

### and Schematic

![schematic](https://github.com/jeanrocco/PI-shutdown-push-button/blob/master/PI_Header_PB_LED_schem.png)

### Pictures

Some pictures might help...

![picture1](https://github.com/jeanrocco/PI-shutdown-push-button/blob/master/20180928_173451.jpg)
![picture2](https://github.com/jeanrocco/PI-shutdown-push-button/blob/master/20180928_173256.jpg)
![picture3](https://github.com/jeanrocco/PI-shutdown-push-button/blob/master/20180928_173220.jpg)

some epoxy glue visible on that one...

![picture4](https://github.com/jeanrocco/PI-shutdown-push-button/blob/master/20180928_172805.jpg)
![picture5](https://github.com/jeanrocco/PI-shutdown-push-button/blob/master/20180928_172744.jpg)


### Python Script

Of course there is a python script that handles it all, copy it in your `/home/pi` directory as [`blink.py`](https://github.com/jeanrocco/PI-shutdown-push-button/blob/master/blink.py.github). 

To start the script `blink.py` at boot, add it to the pi user crontab (`crontab -e`) as:
  
  `@reboot python /home/pi/blink.py &` .
  
###  UPDATE april 20, 2023:
  
  I just installed `Moode 8.3.1`, which comes with an Airplay2 renderer, on a `PI-3b 1.2` equipped with an `IQaudio DAC Pro` HAT. This allows my 2 old mid-2012 MACs, recently upgraded with the wonderfull `https://dortania.github.io/OpenCore-Legacy-Patcher/`, to `VENTURA 13.3.1` no less, to stream music with Airplay2. 
  
  The push button and the led work as before but in order to start the script at boot time you will have to add as root, at the end of  `/etc/rc.local`, and before `exit 0` : `(/home/pi/blink.py)&` as is, with the the brackets and all. I got this from `https://www.msldigital.com/pages/shutdown-scripts-for-moode-audio` .

### UPDATE Nov. 2023: An other update to simplify the previous one...

  After some issues with the Airplay renderers, I found out a simpler setup based on Spotify "connect to a device" feature, that allows to play tunes on the RPI IQaudio DAC, from another computer's browser. 
  First install the latest PI OS (cat /etc/issue => Raspbian GNU/Linux 11 \n \l) on the PI, to make sure the IQaudio DAC is the default audio player change these parameters in /boot/config.txt: 

  Enable audio (loads snd_bcm2835)
#dtparam=audio=on
dtoverlay=iqaudio-dacplus
#dtoverlay=rpi-dacpro
.
.
.
 Enable DRM VC4 V3D driver
dtoverlay=vc4-kms-v3d,noaudio
max_framebuffers=2

  
  jrb.
  

### Enjoy !
