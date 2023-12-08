# Portal 2 PS3 Multiplayer

Here is a quick guide on how to set up Portal 2 PS3 for multiplayer.

1. Download the latest plugin from the [releases page][https://github.com/SourceSPMP/PS3Plugins/releases] on our GitHub
2. Unpack it to an empty folder, let's call that folder `PortalPlugin`
3. Connect to your PS3 via an FTP client (Your PS3 must have a FTP server running on it like WEBMAN)
4. Go to the following directory on your PS3 disk: `dev_hdd0/game/<TITLE ID>/USRDIR/portal2_dlc3/` where `<TITLE ID>` is one of the following:
  * BLUS30732
  * BLES01222
  * BLJM60352
  * BLAS50331
  * BLJM60473
  * NPUB31077
5. Once you are in there, drag the extracted files from the `PortalPlugin` folder, into the `portal2_dlc3` folder.
6. Launch the game and in the main menu, press triangle a bunch of times to open the console.

# Hosting

Do `map mp_coop_lobby_2` and give others your home IP. You have to have port UDP 27015 portforwarded to your PS3.

# Joining

Do `connect <IP>` where `<IP>` is the IP address of the person you are joining.