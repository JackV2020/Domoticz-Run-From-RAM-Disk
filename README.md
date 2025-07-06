# Raspberry Pi complete Domoticz from a ram drive

Domoticz has a very IO intensive database and in the past it was possible to put the logging of that database on a ram drive.

Nowadays that is not supported anymore so you need to run it from your uSD card and wear out that card.

Or.....you run everything from a ram drive.

### Details are described in 'domoticz ramdrive.txt'

The idea behind is that when your Domoticz is NOT running :

 - there is a backup of your domoticz in a seperate backup folder
 - there is a ram drive mounted on your domoticz folder

The /etc/init.d/domoticz.sh when used to start :

 - mounts a ramdisk on the domoticz folder
 - copies the content from the backup folder to the ram drive
 - starts domoticz
 
The /etc/init.d/domoticz when used to stop :

 - stops domoticz
 - copies the content from the ram drive to the backup folder
 - unmounts the ram disk
 
The /etc/init.d/domoticz when used to restart :

 - uses the stop and start so......
 - stops domoticz
 - copies the content from the ram drive to the backup folder
 - no unmount and remount of the ramdisk
 - copies the content from the backup folder to the ram drive
 - starts domoticz

### To save data you may want to create a crontab job to restart your Domoticz every now and then.
