#Change in this fork
This fork was created to work with a Neato vacuum robot. Updates are made to the motor controller file to use the neato_driver.py file from [here](https://github.com/masterhapero/neato_robot/blob/foxy_devel/neato_driver/neato_driver/neato_driver.py) instead of the and I have removed certain features that I was not using.
 
# Configuration
Upon startup, Watney will detect if it's connected to a Wi-Fi hotspot. If not, it will host its own hotspot "Watney".
Once you connect to the hotspot, you can control it directly by going to https://192.168.4.1:5000, or connect it to a Wi-Fi
hotspot by going to http://192.168.4.1 Once you specify your WiFi credentials, Watney will take some time to reboot. Once you hear the startup sound, you're good to go!

Default SSH credentials for Watney are pi / watney5. Watney's mDNS name is watney.local, so if your OS supports mDNS you can simply access it at https://watney.local:5000

Watney's configuration can be found in ~/watney/rover.conf:
* Restart your Watney for configuration changes to take effect

    ## Off Charger re-docking
    Watney can detect when it is taken off the charger outside of its own movement and can attempt to re-dock by driving forward for one second. In my case, Watney occasionally gets knocked off the charger by my Roomba, so enabling this functionality ensures that Watney is always docked and charging. By default this functionality is disabled: I didn't want Watney to drive off someone's workbench while they are working on it. If you'd like to enable this functionality, set `Enabled=True` in the `OFFCHARGER` section of the config.
# Remote Access
Watney has no authentication / security. If you'd like to set it up for remote access, I recommend using [Zerotier](https://www.zerotier.com/). Adding Watney and your client computer to the same Zerotier network will make it appear as if they are on the same local network.

# Building your own Watney image
`packer-builder-arm` is used to build the Watney image. You can find the image build definition in [watney-image.json](packer/watney-image.json). [This article](https://linuxhit.com/build-a-raspberry-pi-image-packer-packer-builder-arm/#:~:text=Packer%2Dbuilder%2Darm%20is%20a,server%20or%20other%20x86%20hardware.) may help setting up `packer` and `packer-builder-arm` on your linux system.

# Raspberry Pi Compatibility
Watney is designed to work with Raspberry Pi 3B, however other versions may be compatible:
* [scifiguy000](https://github.com/scifiguy000) confirmed to have successfully used a Raspberry Pi 4B in [this thread](https://github.com/nikivanov/watney/issues/27)
* Raspberry Pi Zero 2 may work out of the box, but has not been confirmed yet

# Troubleshooting
* Watney works best with Chrome. Other browsers may not work well, or at all.

# Open Source Acknowledgements
The following open source projects were used in development of Watney:
* [Janus WebRTC Server](https://janus.conf.meetecho.com/)
* [GStreamer](https://gstreamer.freedesktop.org/)
* [Raspberry Pi Turnkey](https://github.com/schollz/raspberry-pi-turnkey) 
* [Neato Driver](https://github.com/schollz/raspberry-pi-turnkey) 
