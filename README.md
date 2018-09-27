# PI-shutdown-push-button
A header mounted push button that will safely shutdown the Raspberry PI

This project describes a very simple but very very usefull tool that allow you to safely shutdown your Raspberry PI. This is specially usefull with a headless PI that you cannot connect to because your network/wifi is down... you probably know what I mean... the question is then how to safely shutdown the PI without risking a SD card corruption. 

Now I didn't devised this setup, the credit all goes to [GIMX](https://gimx.fr/wiki/index.php?title=RPi#Autostart_GIMX_at_boot_without_GUI) where I found it. A small advertisement here: GIMX is a cool project that allows old gamers, like me, to use the mouse and keyboard to play games on the PlayStation or XBox. Sounds like a gimmick doesn't it :-) !!!

I thought this was so usefull that I wanted to replicate it here so I would not loose it. 

My meager contribution is repackaging the push button and the led to easily mount them on the PI header.

### Breadboard view

`Fritzing` does not allow the kind of 3D drawing I need to explain how to mount the resistors and the push button (PB) on top of a dual inline 6 pins female header, excuse the distorded view...

![PI_header_BP_led](https://github.com/jeanrocco/PI-shutdown-push-button/blob/master/PI_Header_PB_LED_bb1.png)

### and Schematic

![schematic](https://github.com/jeanrocco/PI-shutdown-push-button/blob/master/PI_Header_PB_LED_schem.png)

### Picture

Final result:

![picture](https://github.com/jeanrocco/PI-shutdown-push-button/blob/master/PB_led_header.png)

### Python Script

Of course there is a python script that handles it all, copy it in your `/home/pi` directory as [`blink.py`](https://github.com/jeanrocco/PI-shutdown-push-button/blob/master/blink.py.github). 

To start the script `blink.py` at boot, add it to the pi user crontab (`crontab -e`) as:
  
  `@reboot python /home/pi/blink.py &` .

