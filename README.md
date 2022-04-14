# Syncthing / SyncTrayzor Setup
This is my walkthrough for setting up Syncthing on unRAID (or any Docker server) and its complementing app SyncTrayzor on Windows

*If you are reading this line then I haven't finished this tutorial yet. This is my first time with GitHub so I'm still working on the markdown syntax. 4/14/22


* Don’t install Syncthing on it’s own. Instead install SyncTrayzor which has syncthing as a part of it.
* It will likely fail to startup Syncthing when launched. Go into Settings→Syncthing→Advanced and add this to the “Syncthing Command-line Flags”
    * -allow-newer-config
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
