# dell-xps-9570-debian
This is not complete but will be updated with time...

Full setup of this dell machine with linux and other machines in a vm, also some basic setups that can be done to tackle some issues that may come about.

Preety basic setup. Im trying to document how I set this machine up, roblems I came accross and potential fixes and how to make it usable at least as a daily driver, maybe an easy enough setup for newbie users like me.

# To do list:

Debian will be installed
Steam will be installed
Gnome boxes for virtualisation
Nvidia proprietary drivers and setup
A little bit of customization to gnome
Firefox touchscreen gestures will be fixed


I have a dell xps 9570, i9-8950HK, 32gb of RAM, 1tb nvme. I have been testing different operating systems and at the moment dont want to have a triple boot, The setup had windows 11, mac os 12, with full touchscreen support, linux was mostly a switch between parrot os and debian Parrot security os was there because I needed to do some vulnerability scanning on some network infrastructure, only problem was that parrot security os always broke something on the machine, I love using gnome, unforuntaely, I could not figure out why the bluetooth audio kept cutting out anytime I stream music from my phone to the laptop through bluetooth, second problem is that the repository is broken and usually holds many broken packages and dependencies, it could just be me who is so lazy and cant figure it out, thereis usually a workaround, it only becomes a problem when it comes up regularly. I tried installing kali, using gnome as the dekstop manager, it was worse, the touch doesnt work and it seemed to be slow, also could be sorted but probably takes a lot of time.


Installing debian is easy, probably not needed to go through the steps but just in case, if this is your only machine, then you could do everything from the machine. First, download the latest version of debian, head over to the debian website, https://www.debian.org/distrib/ as of writing this, current stable version of Debian is 12.6 (bookworm). Select the appropriate architecture, in this case, we use the 64-bit PC netinst.iso. After selecting it, your download should begin and the file should in your downloads folder.
To flash the iso file, ill be using a usb drive. You can use some other media like an external hard drive etc.
You can also use different tools to flash the image to the drive, you can use for example rufus, https://rufus.ie/en/  you can also download balena etcher, https://etcher.balena.io/ and use that, or ventoy if you want to multiboot different isos.
Depending on your tool of choice, here is how to flash an image to a usb drive.
Plug your usb device to the pc, launch rufus.exe after installing. Select device, this will be the usb devbice you have added, in most cases, it will detect it by default, so there should be no worries there.


# Post install
The touchpad seems to be really bad for me, its either I dont know how to use it or the touchpad hardware itself is bad, if you face issues with clicking like me, you can ebale tap to click in the settings, if its not very usable, you can use the toucscreen or an external mouse to access the settings.
First is to pass the welcome screen, select next if the language is correct, next if the keyboard selected is correct. You can turn location services on or off if you wish, i turned mine off, select next after choosing and you can connect accounts if you like, not necessarily compulsory now, you can set it up in the settings later, so I choose skip here. Then all is done.

To enable tap to click, go to settings, on the left panel, look for 'mouse & touchpad* then select 'tap to click'. This will allow tap to click on gnome.
We can install sudo and add our user to the sudo list, this will allow us to run elevated commands without needing to use superuser all the time. to do this, open the terminal, press the windows key, or you can use a 3 finger swipe up on the touchpad and you can type 'terminal' in the keyboard from the overview and you can launch the terminal.
press the command 'su'
It will ask for the password, you will input the root password you selected whenn installing the debian system earlier.
enter the next lines of commands:
apt update
apt upgrade
apt install sudo (mostly instralled by default)
sudo adduser 'input your username here' sudo (in my case, the code is sudo adduser victorf sudo, after this, you will be added to the sudoers list but probably wont work till you logout then log back in or you restart)

# Install steam (skip if you do not want steam)
You can reboot your pc to allow the sudo user to be added or logout and log back in just in case, if not, you may need to use the superuser to do some installations which is not encouraged.

Go to the steam website to download the latest version of steam https://store.steampowered.com/about/. Click install steam and the file will be downloaded. Then you can go to the file manager, locate the downloaded file, right click on an empty space and select 'open in terminal'
![Screenshot from 2024-07-29 15-40-06](https://github.com/user-attachments/assets/5be0d4ca-c739-45ee-af38-c4dc1837095c)

you can use the code below
sudo apt install ./steam_latest.deb
![Screenshot from 2024-07-29 15-45-12](https://github.com/user-attachments/assets/e0f22502-f760-4e85-bde4-fe8854c5bf1e)

new packages will be installed, press y to continue and enter
![Screenshot from 2024-07-29 15-45-57](https://github.com/user-attachments/assets/782598f7-0dbe-4df6-86b9-e962c344362f)

After this, you can find steam under the app lists. Select steam, and there will be some other things to install. Press enter to update the package cache and you will need to input your user password.
![Screenshot from 2024-07-29 15-46-44](https://github.com/user-attachments/assets/56959aab-a659-464e-a5c7-309219156243)

Press enter to continue with installation, press y and press enter to approve the installation.
Press enter to continue

Steam setup will run and will update the runtime environment.
Drink some water/tea/coffee, give it a bit for it to do its thing.
Steam should now be installed and will launch itself, you can now sign in to your steam account.
![Screenshot from 2024-07-29 15-51-17](https://github.com/user-attachments/assets/ccadcd1f-098f-4e99-a6d4-c2c47d8a33f5)

Sometimes it may not allow you to play all your games in your library, and some games probably wont work either, but for the most part, a lot of them should work.
Settings to double check, you can go to 'steam > settings > compatibility' and select enable steam play for all other titles. You will need to restart steam to get this done, but you can select restart later for now, and you should see the option 'run other titles with: proton experimental will be there by default, but may not work for all games, especially if you would like to run some windows exe games directly. In this case, you can tinker around with different proton versions, proton 8.0-5 should be fine, maybe proton 9 works fine also, but I have not tested it, I dont play so many games. Now you can select restart. Steam will restart and you can probably use it to run a few games.
![Screenshot from 2024-07-29 15-53-15](https://github.com/user-attachments/assets/ce5bc86d-333d-490d-8b0e-6539bb5befd8)
 


But we still need to do some other stuff to at least let the graphics card work properly to handle games.
For now, steam can be closed.

# Minimal customization of gnome (This is totally optional and you do not need this, you can also check different ways to customize your gnome setup if you wish)
To customize I will like to add a little bit of customization to gnome as im not much of a fan of its stock look. For this, we already have gnome extensions installed by default so it should be easy.
Simply open firefox, go to the gnome extensions website, https://extensions.gnome.org/ the link should work for a normal debian install, but if that doesnt work, you can try https://extensions-next.gnome.org/ to install. 
In the search bar, type blur my shell, select it and install. Click open link and sleect install, This will give us a blurred look on gnome instantly, which is not much, but at least makes things a little bit nicer.
Go back to the search section and search for 'hide top bar'
select it and install.
Now go to the app menu and search 'extensions' launch extensions and under blur my shell, select settings, go to panel, add the settings in the screenshot.

Close and go back, select settings under hide top bar and choose the following, you can also customize the settings to your wish.

There is a small bug where in some full screen apps, when you take your mouse to the top of the screen, the top bar gets hidden right away, fixing this is easy, you just need to download and install this extra extension Disable unredirect fullscreen windows https://extensions.gnome.org/extension/1873/disable-unredirect-fullscreen-windows/ after installing, the top bar should work just fine.

# Change wallpaper
I downloaded a wallpaper off the internet that I liked, it can be downloaded from here https://wallpapercave.com/w/uwp4451869 
After downloading, navigate to your downloads folder and select the picture, right click on the image and select 'set as background'. After selecting, select 'set'. You should now have a custom wallpaper.

# Fix firefox touchscreen gestures in wayland
To enable proper touch scroll function in firefox, we need to edit a file, simply open the terminal, and use the commands sudo nano /etc/security/pam_env.conf press enter and in the file opened under nano, go to the bottom of the file and add this line MOZ_USE_XINPUT2 DEFAULT=1
Press ctrl+s to save the file and press ctrl+x to close the nano editor. Reboot and on the next launch of firefox, you should have much more responsive touch function.

# Install gnome boxes (not compulsory at all, you probably don't need it unless you want to virtualize windows or some other linux distribution)

Gnome boxes can be used to run and manage virtual machines,
to install this, go to the terminal and use sudo apt install gnome-boxes input your user password, a couple of packages will be added, press y and press enter to continue.
After installation, you can launch gnome boxes from the menu. I probably cannot go further into configuring a virtual machine, but for testing purposes, you can download an iso of a linux distribution.
The downloaded iso can be found imost likely in your downloads folder and should be detected by default in gnome boxes.

Launch gnome boxes, press the plus button to add a virtual machine, it should show the downloaded iso if supported.
Select the right template and if unknown, select unknown os.
Review and create, the error found above; 'virtualization extensions are unavailable on your system' can easily be fixed by going to the terminal and installing install libvirt-clients. We should no longer have this error when setting up a vm again. But we can go back to gnome boxes and allocate the right resources to the machine based on your specs and what you want to give to it.
I will allocate 4gb of ram and 20gb of storage probably can be fine, at least for testing, worst case scenario the storage provisioned is not enough and can be adjusted.
You can allow to inhibit shortcuts or deny. It should launch the machine and you should be able to use it right away.

That's probably how far I can help, at least for now, you can choose to do whatever you'd like with the virtual machine, but you can do the same with windows and with enough tinkering, mac os.








