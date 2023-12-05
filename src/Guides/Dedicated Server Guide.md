{{Author|Whatdidyouexpect & mv}}
# Dedicated Server Guide

# Setup

1. Download SteamCMD
    Details on how to do so are on Valve Developer Wiki [here](https://developer.valvesoftware.com/wiki/SteamCMD#Downloading_SteamCMD)
2. Download files for the game you want to host
    Open command line, run `steamcmd` then follow the steps below carefully
    1. Specify where to install by typing in `force_install_dir /path/to/where/to/put/server`
    2. Login to your steam account by doing `login <username>`, replace "&#60;username&#62;" with your Steam login username
    3. Download the game you want to host for. For example if you want to host for Half-Life 2 you would type in `app_update 220 validate`
    4. Wait for the download to finish and then type in `quit` to exit
3. Download necessary files to turn the game to a dedicated server
    You'll need 2 files to be able to run a dedicated server, srcds executable and the dedicated library file
    You can obtain these files with the following commands:
         Windows: `steamcmd +force_install_dir C:\path\to\where\to\put\temporary\files +login anonymous +download_depot 244310 244312 1190459529383296764 `
         Linux: `steamcmd +force_install_dir /path/to/where/to/put/temporary/files +login anonymous +download_depot 244310 244313 4225323878391996105`
    Note that it HAS to be on a new directory rather than the server directory, we will be copying files from this folder to put into the server
    After downloading, go to the new directory and copy 'srcds_linux' and 'srcds_run' to the server's root and move 'dedicated.so' from 'temorary/files/bin' to the 'server/bin' folder. 
    If you're on Windows, copy 'srcds.exe' to the root and 'dedicated.dll' to the 'bin' folder.
    After you are done, it should look like this:
```
SPMPsrcds
├───bin
│   ├───...
│   └───dedicated.dll
├───hl2
├───platform
├───hl2.exe
├───srcds.exe
├───steam_appid.txt
└───thirdpartylegalnotices.txt
```
  After you are finished, feel free to remove the new folder and continue with the rest of the steps

4. Make a launch script
Create a file named `launch.bat` (`launch.sh` for Linux) with the following contents:
Windows: `srcds.exe -game <gamedir> -console -ip 0.0.0.0 -maxplayers 32`
    Linux:
<pre>
#!/bin/sh
./srcds_run -game &#60;gamedir&#62; -console -ip 0.0.0.0 -maxplayers 32
</pre>
Replace &#60;gamedir&#62; with the folder name for the game you want to host, for example if you are hosting for Half-Life 2 you would have `-game hl2`
After you made the file, launch it. On Linux you'll have to mark the file as executable by running `chmod +x launch.sh` and then launch by doing `./launch.sh`

{{TODO|Have more people try and confirm it's working, also try for Linux, specifically Debian(-based)}}

# Optimization

While the setup will get you started, you'll still need to do some console commands to make the experience more enjoyable.

* `net_splitrate <number bigger than 1, like 10 or 20>` : Will allow the server to send more data per tick.
* `net_splitpacket_maxrate 1048576` : Same as the above.

{{TODO|Talk about engine.dll patches for sv_airaccelerate}}
