# dell-xps-9570-debian
This is not complete but will be updated with time...

Full setup of this dell machine with linux and other machines in a vm, also some basic setups that can be done to tackle some issues that may come about.

Preety basic setup. Im trying to set it up as easy as possible, maybe easy enough for newbie users like me.

To do list:
Debian will be installed
Steam will be installed
Gnome boxes for virtualisation
Nvidia proprietary drivers and setup
A little bit of customization to gnome

I have a dell xps 9570, i9-8950HK, 32gb of RAM, 1tb nvme. I have been testing different operating systems and at the moment dont want to have a triple boot, The setup had windows 11, mac os 12, with full touchscreen support, linux was mostly a switch between parrot os and debian Parrot security os was there because I needed to do some vulnerability scanning on some network infrastructure, only problem was that parrot security os always broke something on the machine, I love using gnome, unforuntaely, I could not figure out why the bluetooth audio kept cutting out anytime I stream music from my phone to the laptop through bluetooth, second problem is that the repository is broken and usually holds many broken packages and dependencies, it could just be me who is so lazy and cant figure it out, thereis usually a workaround, it only becomes a problem when it comes up regularly. I tried installing kali, using gnome as the dekstop manager, it was worse, the touch doesnt work and it seemed to be slow, also could be sorted but probably takes a lot of time.


Installing debian is easy, probably not needed to go through the steps but just in case, if this is your only machine, then you could do everything from the machine. First, download the latest version of debian, head over to the debian website, https://www.debian.org/distrib/ as of writing this, current stable version of Debian is 12.6 (bookworm). Select the appropriate architecture, in this case, we use the 64-bit PC netinst.iso. After selecting it, your download should begin and the file should in your downloads folder.
To flash the iso file, ill be using a usb drive. You can use some other media like an external hard drive etc.
You can also use different tools to flash the image to the drive, you can use for example rufus, https://rufus.ie/en/  you can also download balena etcher, https://etcher.balena.io/ and use that, or ventoy if you want to multiboot different isos.
Depending on your tool of choice, here is how to flash an image to a usb drive.
Plug your usb device to the pc, launch rufus.exe after installing. Select device, this will be the usb devbice you have added, in most cases, it will detect it by default, so there should be no worries there.


post install
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
you can use the code below
sudo apt install ./steam_latest.deb
new packages will be installed, press y to continue and enter
After this, you can find steam under the app lists. Select steam, and there will be some other things to install. Press enter to update the package cache and you will need to input your user password.

Press enter to continue with installation, press y and press enter to approve the installation.

Press enter to continue
Steam setup will run and will update the runtime environment.
Drink some water/tea/coffee, give it a bit for it to do its thing.
Steam should now be installed and will launch itself, you can now sign in to your steam account.
Sometimes it may not allow you to play all your games in your library, and some games probably wont work either, but for the most part, a lot of them should work.
Settings to double check, you can go to 'steam > settings > compatibility' and select enable steam play for all other titles. You will need to restart steam to get this done, but you can select restart later for now, and you should see the option 'run other titles with: proton experimental will be there by default, but may not work for all games, especially if you would like to run some windows exe games directly. In this case, you can tinker around with different proton versions, proton 8.0-5 should be fine, maybe proton 9 works fine also, but I have not tested it, I dont play so many games. Now you can select restart. Steam will restart and you can probably use it to run a few games. But we still need to do some other stuff to at least let the graphics card work properly to handle games.
For now, steam can be closed.

# Minimal customization of gnome (This is totally optional and you do not need this, you can also check different ways to customize your gnome setup if you wish)
To customize I will like to add a little bit of customization to gnome as im not much of a fan of its stock look. For this, we already have gnome extensions installed by default so it should be easy.
Simply open firefox, go to the gnome extensions website, https://extensions.gnome.org/ the link should work for a normal debian install, but if that doesnt work, you can try https://extensions-next.gnome.org/ to install. 
In the search bar, type blur my shell, select it and install. Click open link and sleect install, This will give us a blurred look on gnome instantly, which is not much, but at least makes things a little bit nicer.
Go back to the search section and search for 'hide top bar'
select it and install.
Now go to the app menu and search 'extensions' launch extensions and under blur my shell, select settings, go to panel, add the settings in the screenshot.

Close and go back, select settings under hide top bar and choose the following, you can also customize the settings to your wish.




