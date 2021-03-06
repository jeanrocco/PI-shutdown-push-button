# PI-shutdown-push-button
A header mounted push button that will safely shutdown the Raspberry PI

This project describes a very simple but very very usefull tool that allow you to safely shutdown your Raspberry PI. This might be particularly usefull when, for instance, your headless PI is unreacheable because your network/wifi-router happens to be down at the exact moment you need to shut down the PI ... you probably know what I mean... the question is then how to safely shutdown the PI without risking any SD card corruptions. 

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

### Enjoy !
