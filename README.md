# rpi-videoloop

A simple script to loop a video from USB on boot. 

Based on this article but modified to work with VLC and USB drive.
https://community.spiceworks.com/how_to/135908-loop-a-single-video-on-a-raspberry-pi

## How to

### Step 1
Install VLC and screen
```
sudo apt install vlc
sudo apt install screen
```
### Step 2
Put script in homefolder (/home/pi). Make it executable with
```
chmod +x /home/pi/videoloop 
```
### Step 3
Format a USB drive with exFat, or modify the code to other filesystem. Rename video to 1.mp4 and put in the root folder of the USB drive.
### Step 4
Put this in cron with crontab -e. 
```
@reboot echo "crontab loaded, waiting 10 sec" && sleep 10 && /home/pi/videoloop start
* * * * * echo "Checking if video has stopped" && sleep 1 && /home/pi/videoloop repair 
```

## That's it.
Reboot it and it should start playing on boot.  

## Future development
Rewrite script to look for playlist instead of specific file. 
