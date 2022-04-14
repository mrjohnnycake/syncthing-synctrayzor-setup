# Syncthing / SyncTrayzor Setup

This is my walkthrough for setting up Syncthing on unRAID (or any Docker server) and its complementing app SyncTrayzor on Windows. I felt that the instructions were lacking so hopefully this will help a fellow homelab-er.

*If you are reading this line then I haven't finished this tutorial yet. This is my first time with GitHub so I'm still working on the markdown syntax. 4/14/22

# Install Syncthing on unRAID

* Install Syncthing from the Community Apps repository / page / store / whatever (I used the linuxserver version)
* The default install settings should be fine except you need to app the paths to the server folders you want to sync
* In my case, I want to sync my Windows Downloads folders between my laptop and my office computer. The extra benefit will be that those files will also exist on unRAID so I can then back them up per my server backup scheme. I also had an issue getting this to work with Android so until I get that working I can just connect to my NAS share on unRAID through an Android file browser and get whatever I need out of the Downloads folder and copy it to my phone.
* Click on Add Another Path
	- For the Name, call it whatever makes sense to you as this is what will show in the left hand side of the Syncthing docker config in unRAID
	- For the Container Path, I'm using /data/downloads because when I want to sync another folder I can just use /data/folder-name and it'll keep everything nice and tidy and my OCD will be happy.
	- For Host Path, I have a share called NAS that is my general / go to storage and I created a Downloads folder in there. So my path is /mnt/user/NAS/Downloads/
	- Click Save.


# Setup Syncthing on unRAID

* Open up the Web GUI of the Syncthing by clicking on its icon
* 




# Install and Setup SyncTrayzor on Windows

* Don’t install Syncthing on it’s own. Instead, install SyncTrayzor (which has syncthing as a part of it).
* It will likely fail to startup Syncthing when launched. Go into Settings→Syncthing→Advanced and add this to the “Syncthing Command-line Flags”
    * ```-allow-newer-config```
* It should start up fine now
* Set the GUI username and password (in 1P)
* Add Remote Device in Trayzor
    * Go to the Syncthing install GUI on the server and copy the Device ID with Actions→Show ID
    * Enter that into the Trayzor “Add Device” box under Device ID
    * Leave the Device Name blank
    * On the Sharing tab, click the Introducer and Auto Accept boxes
    * Click Save
* On the server side, accept the connection by allowing in in the pop-up box
* Back in Trayzor, delete the Default folder
* Add a new folder
    * Folder Label: Downloads
    * Folder ID: default (lowercase)
    * Folder Path is the Downloads folder
    * On the Sharing tab, select unRAID
    * Click Save
* On the server side, accept the folder connection by allowing in in the pop-up box
* That’s it for Syncthing. Let it do it’s first time sync before adding any new files
* Trayzor→Settings→SyncTrayzor
    * Minimize to tray
    * Save
