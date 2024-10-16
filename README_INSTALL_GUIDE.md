

-----------------------------------------------------------------------------------------------------------------------
How to run your own WotLK AzerothCore with Playerbots server using Linux (2024)
-----------------------------------------------------------------------------------------------------------------------
Updated: 2024-09-28 (updated AH-BOT db sql line)
Part 1 Installation: https://www.youtube.com/watch?v=DwJ6OfPophw
Part 2 Bot Control: https://www.youtube.com/watch?v=ZGn5BxQeZSw
Part 3 Installing modules: https://www.youtube.com/watch?v=DnHGuZlmdsM
Part 4 Installing ARAC module - All Races All Classes! Undead Hunters!: https://www.youtube.com/watch?v=JjQ-tnk3C2o
Part 5 Auction House Bot module! https://www.youtube.com/watch?v=ZSbvbFAcqzI
-----------------------------------------------------------------------------------------------------------------------

Today I am going to teach you how to run your own World of Warcraft: Wrath of the Lich King server from start to finish using 
Virtualbox and Debian Linux. 
My video is not going to be flashy, but I assure you that I am teaching you just about the best way to do this. 
There are other guides out there on websites and youtube that recommend you run this in Windows using so-called "repacks" but 
as a gamer since 1984, and someone who has ran his own dedicated game servers as far back as the Counterstrike beta, I strongly  
disagree with that way of doing it. Don't just take my word for it - the server we are using - Azerothcore (which is free and open source on github) - agrees with me in their FAQ: https://www.azerothcore.org/wiki/faq

Q. Do you support Repacks based on AzerothCore?
A. No. Repacks are NOT supported and we strongly suggest to not use them for several reasons. You can check this tutorial for an easy way of installing AC without using any repack.
There are a lot of guides out there, but so far I've not seen any of them show you how to install the version with bots to make your server come to life, let alone basic server upkeep, bot control, 
and additional cool things such as the AI voice addon which has narration for the quest text!

-----------------------------------------------------------------------------------------------------------------------
Benefits to running your own WoW server
-----------------------------------------------------------------------------------------------------------------------
Retail World of Warcraft as we all know is a non-stop train - it keeps going and never stops. Private servers, on the other hand, are hosted 
by fans across the world, but they all seem to eventually go offline for one reason or another. They also mostly beg you for money, or are pay to win, and are 
generally for-profit. Azerothcore is completely different. Finally, a group of people decided to collaberate and allow anyone to submit changes and improvements with 
their free and open source model! Although you can use this exact source code to run your own server, we will be using a slightly modified version that allows for bot integration.
The official Azerothcore website is here: https://www.azerothcore.org/
All of the other links are below. I am not a programmer and I have no affiliation with any of the tools we will be using today - I am just a gamer, a fan of World of Warcraft, and a strong supporter of freedom and open source software.

I will try not to get too technical in this tutorial. You should be able to get it up and running as quickly as possible. I could explain every little thing that is going on, but this
tutorial would be several hours long. We can run now and learn later! I tend to be more of a gamer than a knob turner! Self-hosting World of Warcraft gives you god-like 
powers in terms of customization. Here are just some of the control you have in the game:

-Name your realm, assign GMs (game masters), create accounts (and what expansion that account has unlocked, from vanilla to WotLK), and more!
-Install/uninstall any of the dozens of fan-made modules for Azerothcore, such as transmog NPC, skip DK starting zone, account-wide mounts, and more!
-Allow cross-faction grouping, guilding, communication, and raiding. You can even decide to allow all classes for any race, such as a human druid! It's up to you.
-Change bot behavior, item drop rates, gold, boss health, mob health, mob spawn rates and locations. 
-Change and/or disable cooldowns of abilities, debuffs, buffs, and everything else.
-Disable the daze effect (being hit from behind), hearth cooldown, hunter pet happiness, deserter debuff, and everything else! There is almost no limit!
-Keep up to date on future changes of playerbots and Azerothcore or decide to never update and your server will remain static and unchanged! A peaceful, relaxing azeroth that is always available.
-Open the server to remote connections and allow your friends anywhere in the world to connect to you! Or keep it private so only you or those on your home network to connect and play!
-The good feeling that you own your server and it cannot be taken away from you. You own it. Nobody will ask you for money, and Blizzard cannot take your server down. It is really yours.

Why would I want to play with bots?
-Bots make your sever feel alive, even if you're the only human logged into your realm!
-Bots will help you quest, dungeon, and raid. They will heal you, resurrect you,buff you, and even greet you!
-You can decide to have 0 bots, 1 bot, or 1600 bots running around on your realm. It's up to you. 
-"Playerbots" are unique in that they are actual, valid accounts generated on your server. They have real inventories, gear, stats, and gold. 
Unlike "NPCBots," Playerbots can be inspected, traded with, and commanded on a deeper level. For example, you can spawn a Dwarf priest to give yourself the Fear Ward buff! 
-You can immediately change the spec and gear of your bots in your group at any time. You can even summon them to you wherever you are, even in a dungeon, without a warlock! 
I have not tried it, but I'm fairly sure you can summon a real warlock to you and have the warlock cast an actual summoning stone, just like the real thing. 

-----------------------------------------------------------------------------------------------------------------------
Why use my guide?
-----------------------------------------------------------------------------------------------------------------------
I played World of Warcraft from January 2005 to sometime in 2021, mostly as "Painbow-Mal'Ganis," an Orc Hunter. I want to play 
the game as accurately as possible without cheating, but I also want the ability to try interesting things out if I feel like it such as flying to Hyjal (a place you couldn't get to in 3.3.5a), 
or give myself quality of life features such as instant log out. Who ever liked waiting 20 seconds to log out anyway?

-----------------------------------------------------------------------------------------------------------------------
Hardware requirements for the server.
-----------------------------------------------------------------------------------------------------------------------
50GB of hard drive space dedicated to the server
At least a quad core CPU (You could try with less. Not recommended.)
At least 4GB of dedicated memory to the VM (Virtual Machine)

-----------------------------------------------------------------------------------------------------------------------
Software requirements.
-----------------------------------------------------------------------------------------------------------------------
Windows 7, 10, 11
VirtualBox - https://www.virtualbox.org/wiki/Downloads
Debian Bookworm ISO - http://mirror.cogentco.com/debian-cd/current/amd64/iso-cd/
PuTTY (to connect to Debian and issue commands) (get 64-bit x86 version) - https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html
PuTTY (to connect to Debian and issue commands) mirror if above link isn't working: https://abs.freemyip.com:84/share/kd-NUJeO
HeidiSQL (for easy database modifications) - https://www.heidisql.com/download.php?download=installer
WoTLK 3.3.5a client (to play the game) 17GB - https://www.chromiecraft.com/en/downloads/
Unbot addon (to control the bots in-game.) - https://github.com/noisiver/unbot-addon/tree/english
Unbot mirror link if the one above doesn't work: https://abs.freemyip.com:84/share/FD_vJrpt
TipTac tooltip addon: https://felbite.com/addon/4716-tiptac/
TipTac mirror link if above doesn't work: https://abs.freemyip.com:84/api/public/dl/29mVUeau

Optional (although recommended) software:
Patched clients that fix the camera/mouse bug (the one that causes your camera to suddenly jerk in a totally different direction). I HIGHLY recommend this fix!! https://github.com/brndd/vanilla-tweaks/issues/17
VoiceOver addon for World of Warcraft WotLK 3.3.5a: https://github.com/mrthinger/wow-voiceover/releases/download/v1.4.3/AI_VoiceOver-WoW_3.3.5-v1.4.3.zip
VoiceOver vanilla sounds: https://github.com/mrthinger/wow-voiceover/releases/download/v1.3.1/AI_VoiceOverData_Vanilla-v1.0.0.zip


-----------------------------------------------------------------------------------------------------------------------
Getting started. Please watch video for more detail on installing Virtualbox, Debian, and Putty. 
-----------------------------------------------------------------------------------------------------------------------
You can do this even if you know nothing of programming, coding, Linux, operating systems, or anything real complex. You just have to be able to follow my 
instructions exactly. I feel everyone - no matter the skill level - deserves to be able to enjoy running their own server. 

#Install Virtualbox with all the default settings. 
#Install Debian Linux into Virtualbox
#Install putty with default settings. See video guide for all my improvements and settings to all of these.

After installing Virtualbox, Debian, and Putty, we will now use putty to connect to the newly created Debian Linux PC using the username you created during Debian install.
Start by logging into the username you typed in during the Debian install. Let's say it was "nirv" it will appear like this after logging in:

nirv@azeroth:~$

From this point, let's make a password for the root account. 
Root is the "administrator" account. This password can be the same or different from your user you created.

#Change root password
sudo passwd
#don't make the password too large. we'll be typing it frequently

#Now let's log into the root account
su -

Logging into the root account will make your prompt look slightly different than above. 

root@azeroth:~#

#Allow logging in SSH as root directly (you can only SSH into user accounts if you do not change this)
sudo nano /etc/ssh/sshd_config
Permitrootlogin yes
sudo /etc/init.d/ssh restart

#Faster boot
nano /etc/default/grub
GRUB_DEFAULT=1
GRUB_TIMEOUT=0
update-grub

-----------------------------------------------------------------------------------------------------------------------
Force your Debian Linux to keep the same IP address
-----------------------------------------------------------------------------------------------------------------------
#Find your current IP
ip a
#Let's assume it's 192.168.1.250. We will now force debian to keep that IP.

#Find the gateway. usually it's 192.168.1.1
apt install net-tools -y
route -n

#Find the network interface. It's the one that says "UP" here when you use this command. usually it's enp0s3 or something. Let's assume that's it.
ip -br -c link show
#With the current IP, the gateway, and the network interface, let's modify the config.
nano /etc/network/interfaces

#Make sure to comment out or delete the two settings below "the primary network interface" "allow-hotplug" and "iface." We will add the
modifications below that so it's static.

#If you are having connection issues, make sure to set both "gateway" and "dns-nameservers" below to YOUR gateway, which may be 
different from my 192.168.1.1!

# The primary network interface
#allow-hotplug enp0s3
#iface enp0s3 inet dhcp
auto enp0s3
iface enp0s3 inet static
 address 192.168.1.250
 netmask 255.255.255.0
 gateway 192.168.1.1
 dns-domain azeroth.core
 dns-nameservers 192.168.1.1
 
CTRL+O to save and then type exit to close putty. We need to type the next command in the Virtualbox Window
sudo systemctl restart networking.service
 
-----------------------------------------------------------------------------------------------------------------------
#We will now be installing the required software
-----------------------------------------------------------------------------------------------------------------------

apt update && apt upgrade -y
apt update && apt install git curl unzip sudo libreadline-dev -y
git clone https://github.com/liyunfan1223/azerothcore-wotlk.git --branch=Playerbot
cd azerothcore-wotlk
cd modules
git clone https://github.com/liyunfan1223/mod-playerbots.git --branch=master
cd ..
#DEPENDENCIES FOR DEBIAN!!
apt-get update && apt-get install git cmake make gcc g++ clang libssl-dev libbz2-dev libreadline-dev libncurses-dev libboost-all-dev tmux -y
./acore.sh install-deps
./acore.sh compiler all

#allow remote connections for mysql (by remote this means only local networks - not the internet. I would advise enabling this because it allows you to connect to it using HeidiSQL in Windows and modifying 
your database which is much easier than doing it in a Linux terminal!)
nano /etc/mysql/mysql.conf.d/mysqld.cnf
#Scroll all the way down and paste these two lines at the very bottom. Then CTRL+O to save and CTRL+X to exit nano.
bind-address            = 0.0.0.0
mysqlx-bind-address     = 0.0.0.0
sudo systemctl restart mysql

#SQL Database configuration

#create "acore" mysql user
sudo mysql -u root
DROP USER IF EXISTS 'acore'@'localhost';
DROP USER IF EXISTS 'acore'@'127.0.0.1';
CREATE USER 'acore'@'localhost' IDENTIFIED BY 'acore';
CREATE USER 'acore'@'127.0.0.1' IDENTIFIED BY 'acore';
GRANT ALL PRIVILEGES ON * . * TO 'acore'@'localhost' WITH GRANT OPTION;
GRANT ALL PRIVILEGES ON * . * TO 'acore'@'127.0.0.1' WITH GRANT OPTION;
FLUSH PRIVILEGES;
exit;
<press enter>
cd ~/azerothcore-wotlk
./acore.sh client-data
cp env/dist/etc/authserver.conf.dist env/dist/etc/authserver.conf
cp env/dist/etc/worldserver.conf.dist env/dist/etc/worldserver.conf
cd ~/azerothcore-wotlk
#run server to create databases. answer yes to questions. wait till done building then ctrl+z or ctrl+c spam to stop server
./acore.sh run-authserver
ALT+SPACEBAR THEN PRESS D in putty to open a second putty window. Log in root then use the next two commands:
cd ~/azerothcore-wotlk
./acore.sh run-worldserver
#shut down world server. then start auth server. shut down again.

#OPTIONAL REMOTE SQL DATABASE CONNECTION (HeidiSQL)
sudo mysql -u root
#replace the two "nirv" and the "banana" password below with the login/password you would like. This will be entered into your HeidiSQL software in Windows. Connecting this way is visually easier to modify the database for most people.
CREATE USER IF NOT EXISTS 'nirv'@'%' IDENTIFIED BY 'banana';GRANT ALL PRIVILEGES ON *.* TO 'nirv'@'%' WITH GRANT OPTION;
exit;
systemctl restart mysql.service

At this point it's a good idea to shut down the computer by typing this in Linux:
shutdown now
#then manually start it back up by double clicking your debian vm in virtualbox

#SET YOUR SERVER TO BE INTERNET PLAY OR LAN PLAY

#LOCAL ONLY / LAN / YOUR NETWORK ONLY / NO INTERNET ACCESS / SINGLE PLAYER WITH BOTS
#Make sure to put your Linux IP here instead of mine!
#To get your LAN IP, type in putty: ip a
sudo mysql -u root
use acore_auth
UPDATE realmlist SET address = '192.168.1.250' WHERE id = 1;
exit;

#INTERNET / TCP/IP / MULTIPLAYER / ALLOW YOUR FRIENDS TO CONNECT / WAN / OPEN TO INTERNET
#You need to set external IP if you want people to connect to you. ABSOLUTELY NECESSARY OR NOBODY CAN CONNECT!
#To easily obtain your external ip, type this in Putty
curl ipv4.icanhazip.com
#OR
curl ifconfig.me
#Then enter that IP here. THIS IS JUST A SAMPLE. PUT YOUR EXTERNAL IP HERE INSTEAD
sudo mysql -u root
use acore_auth
UPDATE realmlist SET address = '66.24.137.208' WHERE id = 1;
exit;
#OR IF YOU HAVE A DDNS
sudo mysql -u root
use acore_auth
UPDATE realmlist SET address = 'dns.bobsaget.com' WHERE id = 1;
exit;

#YOU CAN CHANGE YOUR REALM NAME AT ANY TIME WITH THIS COMMAND
sudo mysql -u root
use acore_auth
UPDATE realmlist SET name = 'World of Gangstalking' WHERE id = 1;
exit;

#Optional. If you are going to allow friends to connect to your server, you have to open the following two ports in your router. 
Port forward: 
3724 TCP AUTH
8085 TCP WORLD

#We must make a start.sh script right now to make starting and stopping our server easier. 
nano /root/start.sh
#Now take all text below and paste it into the new document we just made. Then save it with CTRL+O
authserver="~/azerothcore-wotlk/acore.sh run-authserver"
worldserver="~/azerothcore-wotlk/acore.sh run-worldserver"

authserver_session="auth-session"
worldserver_session="world-session"

if tmux new-session -d -s $authserver_session; then
    echo "Created authserver session: $authserver_session"
else
    echo "Error when trying to create authserver session: $authserver_session"
fi

if tmux new-session -d -s $worldserver_session; then
    echo "Created worldserver session: $worldserver_session"
else
    echo "Error when trying to create worldserver session: $worldserver_session"
fi

if tmux send-keys -t $authserver_session "$authserver" C-m; then
    echo "Executed \"$authserver\" inside $authserver_session"
    echo "You can attach to $authserver_session and check the result using \"tmux attach -t $authserver_session\""
else
    echo "Error when executing \"$authserver\" inside $authserver_session"
fi

if tmux send-keys -t $worldserver_session "$worldserver" C-m; then
    echo "Executed \"$worldserver\" inside $worldserver_session"
    echo "You can attach to $worldserver_session and check the result using \"tmux attach -t $worldserver_session\""
else
    echo "Error when executing \"$worldserver\" inside $worldserver_session"
fi
#END OF SCRIPT. 

-----------------------------------------------------------------------------------------------------------------------
Now you must use these Linux aliases to give you easy shortcuts for starting, stopping, and updating the server with ease!
-----------------------------------------------------------------------------------------------------------------------

nano ~/.bashrc

#START
alias wow='cd ~/azerothcore-wotlk;tmux attach -t world-session'
alias auth='cd ~/azerothcore-wotlk;tmux attach -t auth-session'
alias start='bash /root/start.sh'
alias stop='tmux kill-server'
alias compile='cd ~/azerothcore-wotlk;./acore.sh compiler all'
alias build='cd ~/azerothcore-wotlk;./acore.sh compiler build'
alias update='cd ~/azerothcore-wotlk;git pull;cd ~/azerothcore-wotlk/modules/mod-playerbots;git pull'
alias pb='nano ~/azerothcore-wotlk/env/dist/etc/modules/playerbots.conf'
alias world='nano ~/azerothcore-wotlk/env/dist/etc/worldserver.conf'
#END

source ~/.bashrc

Now we can start and stop our server with ease simply by typing start or stop anywhere in Linux! Let's start it:
start

You can now view the world-server in putty any time your server is running by typing:
wow

And you can see the auth server any time it's running by typing:
auth

Let's type wow to get into the world-server session where we can issue commands.
wow

#Note. If you want to exit the "world session" screen (with the green bar across the bottom), press CTRL+B and then press D to "detatch" from the tmux session. (This is the technical term for what's going on.) 
#If this is too difficult to remember or too cumbersome, you can always just close the putty terminal here.

-----------------------------------------------------------------------------------------------------------------------
Creating your first account and giving him GM powers
-----------------------------------------------------------------------------------------------------------------------
Create your account from the world session tmux terminal:
account create <username> <password>
account create nirv banana
account set gmlevel nirv 3 -1

Now is a good time to download the WotLK 3.3.5a client. I advise you extract this 17GB folder to your fastest drive. Download it here:
https://www.chromiecraft.com/en/downloads/

-----------------------------------------------------------------------------------------------------------------------
Setting the IP address in your 3.3.5a WoW client so you can connect to the server!
-----------------------------------------------------------------------------------------------------------------------
We need to allow the client to connect to our server now by modifying the realmlist.wtf file, located in \Data\enUS\ in your ChromieCraft folder.
#in my case
C:\ChromieCraft_3.3.5a\Data\enUS\realmlist.wtf
set realmlist 192.168.1.250
Open wow.exe, type your username and password for the account you just created and connect!

You should now be able to log in and play with your bots immediately. 

-----------------------------------------------------------------------------------------------------------------------
Script to fix your bots rejecting your invite! This is also good for deleting and purging all your bots and their data. This will not delete human players or data - only bots.
Added 2024-07-04
-----------------------------------------------------------------------------------------------------------------------
If you try adding a box and they whisper you "Hello!" "Goodbye!" immediately, deleting your bot accounts and purging their data can fix it using the following script:

#First, stop your server
cd ~/
wget https://abs.freemyip.com:84/api/public/dl/tMI5q0Kq?inline=true -O cleanbots-rc03.sql
mysql -u root
source ~/cleanbots-rc03.sql
exit;

#start your server back up
start

Your bots should now accept your invite. 
Video of this happening to me and this fixing it: https://youtu.be/x6ojQdEDDpM?t=1893
-----------------------------------------------------------------------------------------------------------------------


Now let's edit the config files. One is for the world server and the other is for bots.

WORLD SERVER CONFIG:
nano ~/azerothcore-wotlk/env/dist/etc/worldserver.conf
#Or if you used the aliases above, you can just type world from now on from anywhere in Linux to access this config file!

Here are my recommended settings for the world server:
GameType = 1
Quests.IgnoreRaid = 1
MonsterSight = 20.000000
ListenRange.Say = 80
Instance.GMSummonPlayer = 1
AccountInstancesPerHour = 20
MailDeliveryDelay = 0
LeaveGroupOnLogout.Enabled = 1
StrictNames.Reserved = 0
StrictNames.Profanity = 0
MaxGroupXPDistance = 1000
InstantLogout = 0
Visibility.Distance.Continents = 120
Visibility.Distance.Instances = 200
MapUpdate.Threads = 2
Quests.EnableQuestTracker = 1
MaxPrimaryTradeSkill = 11
PlayerLimit = 0
MaxWhoListReturns = 49
PacketSpoof.Policy = 0
Warden.Enabled = 0
MaxRecruitAFriendBonusDistance = 1000
ChatFakeMessagePreventing = 1
ChatFlood.MessageCount = 0
AllowTwoSide.Accounts = 1
AllowTwoSide.Interaction.Chat = 0
PreventAFKLogout = 2

PLAYERBOT CONFIG:
#First let's copy the distconf file to a real config file. This only has to be done once!
cp ~/azerothcore-wotlk/env/dist/etc/modules/playerbots.conf.dist ~/azerothcore-wotlk/env/dist/etc/modules/playerbots.conf
#From now on we will use the command below to modify our playerbots config! 
#Or if you used the aliases above, you can just type pb from now on from anywhere in Linux to access this config file!
nano ~/azerothcore-wotlk/env/dist/etc/modules/playerbots.conf
Here are my recommended settings for playerbots:
AiPlayerbot.RandomBotAutologin = 1
AiPlayerbot.RandomBotLoginAtStartup = 0
AiPlayerbot.MinRandomBots = 400
AiPlayerbot.MaxRandomBots = 500
AiPlayerbot.RandomBotMinLevel = 1
AiPlayerbot.RandomBotMaxLevel = 80
AiPlayerbot.EnableRotation = 0
AiPlayerbot.RandomBotAccountCount = 240
#reset bot database by setting the following command to 1, save, start server, quickly set this back to 0, save, and that's it. Otherwise normally leave this at 0.
#AiPlayerbot.DeleteRandomBotAccounts = 1
AiPlayerbot.RandomBotMaxLevelChance = 0
AiPlayerbot.EnableGreet = 0
AiPlayerbot.SummonWhenGroup = 0
AiPlayerbot.RandomBotShowHelmet = 0
AiPlayerbot.RandomBotShowCloak = 1
AiPlayerbot.DisableRandomLevels = 1
AiPlayerbot.RandombotStartingLevel = 1
AiPlayerbot.KillXPRate = 1
AiPlayerbot.BotActiveAlone = 100
AiPlayerbot.RandomBotGroupNearby = 1
AiPlayerbot.RandomBotSayWithoutMaster = 0
AiPlayerbot.EquipmentPersistence = 0
AiPlayerbot.EquipmentPersistenceLevel = 80
AiPlayerbot.AutoPickReward = yes
AiPlayerbot.AutoTeleportForLevel = 1
AiPlayerbot.AutoDoQuests = 1
PlayerbotsDatabase.WorkerThreads     = 4
PlayerbotsDatabase.SynchThreads     = 4
AiPlayerbot.MinRandomBotTeleportInterval = 93600
AiPlayerbot.MaxRandomBotTeleportInterval = 108000
AiPlayerbot.RandomBotAutoJoinBG = 1
AiPlayerbot.ProbTeleToBankers = 0.25
AiPlayerbot.AddClassCommand = 1
AiPlayerbot.BotAutologin = 0
AiPlayerbot.GroupInvitationPermission = 2
#the following command is currently bugged. if you set less than 1.1, your bots will be nude/naked/have no gear when you initialize them. HOPE IT'S FIXED SOON.
AiPlayerbot.AutoInitEquipLevelLimitRatio = 1.1
AiPlayerbot.AutoInitOnly = 0
#bot controlability
AiPlayerbot.SelfBotLevel = 2
AiPlayerbot.SyncLevelWithPlayers = 0
AiPlayerbot.BotReviveWhenSummon = 2
AiPlayerbot.FreeMethodLoot = 0
AiPlayerbot.FreeFood = 1
AiPlayerbot.AutoEquipUpgradeLoot = 1
AiPlayerbot.MaintenanceCommand = 1
AiPlayerbot.AutoAvoidAoe = 1
AiPlayerbot.TellWhenAvoidAoe = 1
AiPlayerbot.SummonAtInnkeepersEnabled = 1

One final thing to hide the Debian VM to run in the background from now on. 
Open Windows Explorer
Navigate to C:\Program Files\Oracle\VirtualBox
In the File Explorer address bar, type cmd and press enter. From here, assuming you named your Debian machine in virtualbox "Azeroth" paste the following command here. Match the name to the name of your VM.
From now on when you start the debian PC it will always run headless, or in the background. You can even close Virtualbox itself!
#Note - Debian must be shut down before you run this command. shutdown now to shutdown in Linux
VBoxManage modifyvm "Azeroth" --defaultfrontend headless

Keyboard shortcuts/hotkeys to get used to:
Putty:
ALT+SPACE then D to open a new SSH window to the Linux PC.
Linux Terminal:
#start the wow server
start
#stop the wow server
stop
#connect to the wow-server session (to issue commands outside of the game)
wow
#connect to the auth-server session
auth
#update update azerothcore + playerbot modules from github. could be daily, could be hourly even. 
update
#build/create new server files. only do this after updating or modifying the source code itself for deep changes, or module additions
#note: you can compile while your server is still up. but for the changes to take effect, always stop and start your server after compiling is complete
build
#compile from scratch (takes longer. mostly not necessary)
compile
#access and modify your playerbots config
pb
#access and modify your worldserver config
world
CTRL+C to stop process or clear the line
CTRL+Z to stop certain processes 
CTRL+O to save text or config file while open in nano
CTRL+X to close text or config file while in nano
CTRL+W to search while in nano
CTRL+X then press N for NO to exit nano without saving (in case you fucked up the text)
clear to clear the terminal screen

#use the following command to wipe the temporary source build directory. useful to do once in a while, especially if you have issues compiling.
rm -rf /root/azerothcore-wotlk/var/build

-----------------------------------------------------------------------------------------------------------------------
LINKS
This installation guide: https://abs.freemyip.com:84/api/public/dl/dOIVokJQ/installation.txt?inline=true
The modified fork of Azerothcore that we are using: https://github.com/liyunfan1223/azerothcore-wotlk
Playerbots module that we use: https://github.com/liyunfan1223/mod-playerbots
WoW addons for 3.3.5a WotLK client: https://felbite.com/chromiecraft-addons/

GM Commands (HUGE list here. Most of these work in-game if you are a GM but you need a period in the front. For example, ".account onlinelist." You do not need the period if you type in the "world-session"
window in Linux (accessed by typing wow). "account onlinelist"
In-Game: .account onlinelist
World-Session Window: account onlinelist
I hope this makes sense to you.
In-Game:  .server shutdown 20
World-Session Window: server shutdown 20
#Give yourself a large 36 slot bag (GM only)
.add 23162

PuTTY settings:
Columns: 120
Rows: 35
Lines of scrollback: 2000
Font: Courier New, 26-point
Behavior: System menu appears on alt-space

---------------------------------------------------------------------------------------
Part 3 - Installing modules like account-wide mounts and no hearth cooldown!
---------------------------------------------------------------------------------------
List of Azerothcore modules:
https://www.azerothcore.org/catalogue.html#/
---------------------------------------------------------------------------------------
Installing our first module
Module: mod-no-hearthstone-cooldown
https://www.azerothcore.org/catalogue.html#/details/413896014
Press "View on Github" on the right of the page.
Press the green "Code" button and then copy the URL to clipboard. 
Log into Linux using Putty
#copy and paste the following command to go to your modules directory
cd ~/azerothcore-wotlk/modules/
#use the gitclone link you copied and paste it after typing "git clone" like so
git clone https://github.com/BytesGalore/mod-no-hearthstone-cooldown.git
#recompile your server by entering the following commands
cd ~/azerothcore-wotlk
./acore.sh compiler build
#Note: If this doesn't work, just type the word compile in Linux. If you followed my guide, "compile" is an alias that will recompile your entire acore server, which takes longer but is complete. 

Modifying the config
#first copy the conf.dist to a new file and edit that, like so
cp ~/azerothcore-wotlk/env/dist/etc/modules/mod_no_hearthstone_cooldown.conf.dist ~/azerothcore-wotlk/env/dist/etc/modules/mod_no_hearthstone_cooldown.conf
#edit the newly copied file
nano ~/azerothcore-wotlk/env/dist/etc/modules/mod_no_hearthstone_cooldown.conf
#when finished, ctrl+o to save changes then ctrl+x to exit. now you must restart your wow server for changes to take effect
stop
start
---------------------------------------------------------------------------------------
Module: mod-account-mounts
cd ~/azerothcore-wotlk/modules/
git clone https://github.com/azerothcore/mod-account-mounts
#if you wish to share mounts cross-faction, change the following to limitrace = false. Otherwise, just continue with compiling
#nano ~/azerothcore-wotlk/modules/mod-account-mounts/src/mod_account_mount.cpp
cd ~/azerothcore-wotlk/
./acore.sh compiler build
cp ~/azerothcore-wotlk/env/dist/etc/modules/mod_account_mount.conf.dist ~/azerothcore-wotlk/env/dist/etc/modules/mod_account_mount.conf
#modify the config file if necessary
nano ~/azerothcore-wotlk/env/dist/etc/modules/mod_account_mount.conf
#restart server to take effect!
stop
start

---------------------------------------------------------------------------------------
Part 4 - Installing ARAC module - All Races All Classes. Allows for any race to be any class. Human druids, undead hunters, Gnome Paladins. 
---------------------------------------------------------------------------------------
I do not know how to reverse this installation so if it messes something up, you are on your own!
https://www.azerothcore.org/catalogue.html#/details/236337938

#log into linux server with putty then clone ARAC repository
cd ~/azerothcore-wotlk/modules
git clone https://github.com/heyitsbench/mod-arac.git
cp ~/azerothcore-wotlk/modules/mod-arac/patch-contents/DBFilesContent/* ~/azerothcore-wotlk/env/dist/bin/dbc

sudo mysql -u root
use acore_world
source ~/azerothcore-wotlk/modules/mod-arac/data/sql/db-world/arac.sql;
exit;
Now just compile!
cd ~/azerothcore-wotlk/
./acore.sh compiler build
#restart server for changes to take effect
stop
start

Now download this file in windows and put it in your wow folder/data folder!
https://github.com/heyitsbench/mod-arac/raw/master/Patch-A.MPQ
---------------------------------------------------------------------------------------

-----------------------------------------------------------------------------------------------------------------------
Part 5 - Installing Auction House Bot module (AHBOT)
-----------------------------------------------------------------------------------------------------------------------
https://www.azerothcore.org/catalogue.html#/details/138432861

Install HeidiSQL installer (easier): https://www.heidisql.com/download.php
#If you don't want to install it, you can download the portable 64-bit edition and extract the zip file.
Leave HeidiSQL open. We will return to it.

#log into linux server with putty then clone ah-bot repository
cd ~/azerothcore-wotlk/modules
git clone https://github.com/azerothcore/mod-ah-bot.git

#import the sql file for this mod
sudo mysql -u root
use acore_world
source ~/azerothcore-wotlk/modules/mod-ah-bot/data/sql/db-world/mod_auctionhousebot.sql;
exit;

#We must now create a new SQL account so we can access our database using HeidiSQL. This will only be used for HeidiSQL connections
sudo mysql -u root
#You can change the two 'nirvs' below but they must match. Change the 'password' below as well. This will be entered into your HeidiSQL software in Windows. Connecting this way is visually easier to modify the database for most people.
CREATE USER IF NOT EXISTS 'nirv'@'%' IDENTIFIED BY 'password';GRANT ALL PRIVILEGES ON *.* TO 'nirv'@'%' WITH GRANT OPTION;
exit;
systemctl restart mysql.service

#Now compile!
cd ~/azerothcore-wotlk/
./acore.sh compiler build

#Now you need to make an account and then a character who will be the one posting the auctions. This will be the name of the seller that you see on the AH in game. You can name any of these any name you want.
wow
account create ahbot password
Log into this account in-game then create your ahbot character. This will be the name that appears as the seller name on the AH. This char is strictly for AH - don't log into it after this. Addons selected don't matter.
Log out.

#We must now log into our database with HeidiSQL to identify the account and the GUID of the new character we made so we can enter them into the ahbot config file.
#Use the account we just created 3 steps ago for the login/password field in HeidiSQL. 
#If you forgot the IP address of your Linux server, just type ip a while in putty to get your IP. This is the one we will put into HeidiSQL.
acore_auth -> account -> get the account id of new account: 203
acore_characters -> characters -> get the GUID 

#We must now copy and edit the ahbot config file.
cp ~/azerothcore-wotlk/env/dist/etc/modules/mod_ahbot.conf.dist ~/azerothcore-wotlk/env/dist/etc/modules/mod_ahbot.conf

#use this line from now on to adjust this module's settings! You MUST edit this file because everything is disabled by default in it!!
nano ~/azerothcore-wotlk/env/dist/etc/modules/mod_ahbot.conf

#the settings I use. Make sure to change the AH bot account number and the character GUID below to yours. Everyones will be different. You can find this information in the HeidiSQL step above.
AuctionHouseBot.DEBUG = 0
AuctionHouseBot.DEBUG_FILTERS = 0
AuctionHouseBot.EnableSeller = 1
AuctionHouseBot.EnableBuyer = 1
AuctionHouseBot.UseBuyPriceForSeller = 0
AuctionHouseBot.UseBuyPriceForBuyer = 0
AuctionHouseBot.Account = 204
AuctionHouseBot.GUID = 2018
AuctionHouseBot.ItemsPerCycle = 1200

AuctionHouseBot.VendorItems = 0
AuctionHouseBot.VendorTradeGoods = 1
AuctionHouseBot.LootItems = 1
AuctionHouseBot.LootTradeGoods = 1
AuctionHouseBot.OtherItems = 0
AuctionHouseBot.OtherTradeGoods = 1
AuctionHouseBot.No_Bind = 1
AuctionHouseBot.Bind_When_Picked_Up = 0
AuctionHouseBot.Bind_When_Equipped = 1
AuctionHouseBot.Bind_When_Use = 1
AuctionHouseBot.Bind_Quest_Item = 0
AuctionHouseBot.DisablePermEnchant = 0
AuctionHouseBot.DisableConjured = 0
AuctionHouseBot.DisableGems = 0
AuctionHouseBot.DisableMoney = 0
AuctionHouseBot.DisableMoneyLoot = 0
AuctionHouseBot.DisableLootable = 0
AuctionHouseBot.DisableKeys = 0
AuctionHouseBot.DisableDuration = 0
AuctionHouseBot.DisableBOP_Or_Quest_NoReqLevel = 0

AuctionHouseBot.DisableWarriorItems = 0
AuctionHouseBot.DisablePaladinItems = 0
AuctionHouseBot.DisableHunterItems = 0
AuctionHouseBot.DisableRogueItems = 0
AuctionHouseBot.DisablePriestItems = 0
AuctionHouseBot.DisableDKItems = 0
AuctionHouseBot.DisableShamanItems = 0
AuctionHouseBot.DisableMageItems = 0
AuctionHouseBot.DisableWarlockItems = 0
AuctionHouseBot.DisableUnusedClassItems = 0
AuctionHouseBot.DisableDruidItems = 0

AuctionHouseBot.DisableItemsBelowLevel = 0
AuctionHouseBot.DisableItemsAboveLevel = 0
AuctionHouseBot.DisableTGsBelowLevel = 0
AuctionHouseBot.DisableTGsAboveLevel = 0
AuctionHouseBot.DisableItemsBelowGUID = 0
AuctionHouseBot.DisableItemsAboveGUID = 0
AuctionHouseBot.DisableTGsBelowGUID = 0
AuctionHouseBot.DisableTGsAboveGUID = 0
AuctionHouseBot.DisableItemsBelowReqLevel = 0
AuctionHouseBot.DisableItemsAboveReqLevel = 0
AuctionHouseBot.DisableTGsBelowReqLevel = 0
AuctionHouseBot.DisableTGsAboveReqLevel = 0
AuctionHouseBot.DisableItemsBelowReqSkillRank = 0
AuctionHouseBot.DisableItemsAboveReqSkillRank = 0
AuctionHouseBot.DisableTGsBelowReqSkillRank = 0
AuctionHouseBot.DisableTGsAboveReqSkillRank = 0

#Adjust total number of auctions on the AH. I currently use 25,000!
sudo mysql -u root
UPDATE acore_world.mod_auctionhousebot SET maxitems = 25000, minitems = 25000 WHERE auctionhouse = 2 OR auctionhouse = 6 OR auctionhouse = 7 ;
exit;

#LINK ALL 3 AUCTION HOUSES [Optional but advised]
#You can link all 3 auction houses (Alliance, Horde, and Neutral) by changing the following setting to 1 in your worldserver config file. I currently do this.
nano ~/azerothcore-wotlk/env/dist/etc/worldserver.conf
AllowTwoSide.Interaction.Auction = 1

Reset your server an the AH should be populated! 
stop
start
END OF GUIDE!

#delete all auctions from AH database (just in case you want a total refresh or if you want to delete your ah bot account and all the auctions)
mysql -u root
USE acore_characters
DELETE FROM auctionhouse;
exit;
-----------------------------------------------------------------------------------------------------------------------

-----------------------------------------------------------------------------------------------------------------------
Part 6 - Create your own flying mount that works everywhere!
-----------------------------------------------------------------------------------------------------------------------
#First stop your server if it's running
stop

#add it to the database

sudo mysql -u root
use acore_world

DELETE FROM `item_template` WHERE `entry`=701000;

INSERT INTO `item_template` (`entry`, `class`, `subclass`, `SoundOverrideSubclass`, `name`, `displayid`, `Quality`, `Flags`, `FlagsExtra`, `BuyCount`, `BuyPrice`, `SellPrice`, `InventoryType`, `AllowableClass`, `AllowableRace`, `ItemLevel`, `RequiredLevel`, `RequiredSkill`, `RequiredSkillRank`, `requiredspell`, `requiredhonorrank`, `RequiredCityRank`, `RequiredReputationFaction`, `RequiredReputationRank`, `maxcount`, `stackable`, `ContainerSlots`, `StatsCount`, `stat_type1`, `stat_value1`, `stat_type2`, `stat_value2`, `stat_type3`, `stat_value3`, `stat_type4`, `stat_value4`, `stat_type5`, `stat_value5`, `stat_type6`, `stat_value6`, `stat_type7`, `stat_value7`, `stat_type8`, `stat_value8`, `stat_type9`, `stat_value9`, `stat_type10`, `stat_value10`, `ScalingStatDistribution`, `ScalingStatValue`, `dmg_min1`, `dmg_max1`, `dmg_type1`, `dmg_min2`, `dmg_max2`, `dmg_type2`, `armor`, `holy_res`, `fire_res`, `nature_res`, `frost_res`, `shadow_res`, `arcane_res`, `delay`, `ammo_type`, `RangedModRange`, `spellid_1`, `spelltrigger_1`, `spellcharges_1`, `spellppmRate_1`, `spellcooldown_1`, `spellcategory_1`, `spellcategorycooldown_1`, `spellid_2`, `spelltrigger_2`, `spellcharges_2`, `spellppmRate_2`, `spellcooldown_2`, `spellcategory_2`, `spellcategorycooldown_2`, `spellid_3`, `spelltrigger_3`, `spellcharges_3`, `spellppmRate_3`, `spellcooldown_3`, `spellcategory_3`, `spellcategorycooldown_3`, `spellid_4`, `spelltrigger_4`, `spellcharges_4`, `spellppmRate_4`, `spellcooldown_4`, `spellcategory_4`, `spellcategorycooldown_4`, `spellid_5`, `spelltrigger_5`, `spellcharges_5`, `spellppmRate_5`, `spellcooldown_5`, `spellcategory_5`, `spellcategorycooldown_5`, `bonding`, `description`, `PageText`, `LanguageID`, `PageMaterial`, `startquest`, `lockid`, `Material`, `sheath`, `RandomProperty`, `RandomSuffix`, `block`, `itemset`, `MaxDurability`, `area`, `Map`, `BagFamily`, `TotemCategory`, `socketColor_1`, `socketContent_1`, `socketColor_2`, `socketContent_2`, `socketColor_3`, `socketContent_3`, `socketBonus`, `GemProperties`, `RequiredDisenchantSkill`, `ArmorDamageModifier`, `duration`, `ItemLimitCategory`, `HolidayId`, `ScriptName`, `DisenchantID`, `FoodType`, `minMoneyLoot`, `maxMoneyLoot`, `flagsCustom`, `VerifiedBuild`) VALUES (701000, 9, 0, -1, 'Tome of World Flying', 61330, 7, 134217792, 0, 1, 4500000, 4500000, 0, -1, -1, 80, 45, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1000, 0, 0, 483, 0, -1, 0, -1, 0, -1, 31700, 6, 0, 0, -1, 0, -1, 0, 0, 0, 0, -1, 0, -1, 0, 0, 0, 0, -1, 0, -1, 0, 0, 0, 0, -1, 0, -1, 0, 'Learn to fly everywhere', 0, 0, 0, 0, 0, 8, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, -1, 0, 0, 0, 0, '', 0, 0, 0, 0, 0, 1);

exit;

#start server up and enter the game
start

#must be a GM and be targeting yourself or whoever you are giving it to
.additem 701000

Learn it and then check your mounts window (Shift+P)
Have fun!

-----------------------------------------------------------------------------------------------------------------------

Some notes worth knowing. I learned these from my own experience or talking to devs on discord:
Playerbots ignore PvE rules, so for now it's easiest to stick to a pvp server. (the bots can attack you but you can't attack back in pve. Change to a pvp server in worldserver.conf)
"You don't need to mess around with threads except mapupdate" --Revision
Bot limit seems to vary for unknown reasons. Some people have issues with 500 bots, others can seem to handle 4000. Personally, I don't go above 1200 bots or I start to have issues. Performance improvements are always changing.
Azerothcore devs have stated that they will stop supporting mariadb sometime in the future, so I will recommend using the mysql install with azerothcore. 







