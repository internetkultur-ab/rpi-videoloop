# rpi-videoloop

A simple script to loop a video from USB on boot. 

Based on this article but modified to work with VLC and USB drive.
https://community.spiceworks.com/how_to/135908-loop-a-single-video-on-a-raspberry-pi

# Usage
Download code and make it executable. Start with ./videoloop start. Cronjob on boot to start it and a cronjob every minute to see if VLC has crasched. Expects an USB drive formatted in exFat with only one partition and will play file named 1.mp4.

# cronjobs
Put this in cron with crontab -e. 
```
@reboot echo "crontab loaded, waiting 10 sec" && sleep 10 && /home/pi/videoloop start
* * * * * echo "Checking if video has stopped" && sleep 1 && /home/pi/videoloop repair
```

# Future development
Rewrite script to look for playlist instead of specific file. 
