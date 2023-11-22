# The Orange Box (PS3)

The Orange Box port for the PS3 was made by EA back in December 11th 2007.

---

# File structure

It uses a completely alien structure (to the source engine) with the entire game being stored in a single .SELF(executable like .exe) file and assets being stored per map rather than a giant package. (except for sounds and "extra_game_data")
Extraction of the .GRP files is yet to be done.

Luckily, the game still tries to access the normal file system which allows for custom CFG files to be loaded and executed by the game.

# Custom configs

The user config (saved in `/dev_hdd0/home/00000001/savedata/BLES00153-<game name>CONF-0/`) is protected by a CRC32 checksum which can be easily modified with a hex editor. Simply get the CRC32 checksum of the .CFG file inside, and put it in the first 4 bytes of the .CHK file (big-endian order). With that, you can rebind one of your buttons (like SELECT which is named "BACK") to execute a config.

Remember that the **PS3 file system is case-sensitive** so you cant access "TEST.CFG" with "test.cfg". This goes for everything like maps and other things.

You can bind your select button to `exec TEST.CFG`, and put a file named `TEST.CFG` inside `<game dir>/USRDIR/GAME/<game name like HL2>/CFG/`. This will make it easier to execute commands at will because the files inside the `CFG` folder do not have a checksum.

I personally recommend making `TEST.CFG` rebind your buttons to execute whatever commands you need (like binding X to noclip) and making a second config called `NORMAL.CFG` which binds the buttons to the default gameplay configuration. That way, you can make `TEST.CFG` bind SELECT to `exec NORMAL.CFG` and `NORMAL.CFG` bind SELECT to `exec TEST.CFG`. (you can also make more configs which you switch between, sky is the limit)

---

# File system trick

You can make Source save to any file in your hard drive, because the path filter does not account for the PS3 not having disk drive names for global paths. Meaning you can just save any file (like a log) to `/dev_hdd0/` by just passing the raw path into a convar which will do that.

# TF2 trick

Because EA servers are down, you shouldn't be able to play TF2 anymore, but you can use `map_commentary` inside `MODSETTINGS.CFG` to load a map with (or without if you have a patch) commentary nodes. Make sure to have the proper case of the map name. This will go around the EA connection dialog but beware, when you pause the game, it will try to connect.

---

# What works

* `log on/off`
* `cl_showfps 1`
* `sv_cheats 1`
* `noclip`
* `god`
* `mat_motion_blur_enabled 0`
* `fps_max 300` (Will actually give you more fps which is really nice!)

# What does not

* `showconsole`, `toggleconsole` etc.
* Anything that prints to the console (EA removed every `Msg()` and similar functions)

# What crashes the game

* Most shader related commands like `mat_fullbright 1` will crash the game because EA did not compile the proper shaders for them to save space.
* Without a patch, `maxplayers >1` will crash the game when creating a server on a SP branch game.
* Without a patch, `map_commentary` will crash the game when loading a map that doesnt have commentary nodes.

---

The Orange Box for the PS3 is still being researched. Join our [Discord][https://discord.gg/xPxqeND8gQ] if you want to contribute or ask questions.