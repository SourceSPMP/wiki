{{Author|Whatdidyouexpect & mv}}
# Dedicated Server Guide

1. Download HL2:DM Dedicated Server (`steamcmd +force_install_dir /path/to/where/to/put/srcds +login anonymous +app_update 238430 validate +quit`)
2. Copy desired game folder to root directory of the dedicated server (i.e. `hl2`, `ep1`, `episodic`, `portal`)
3. Copy `engine.so` (`engine.dll` for Windows) from bin into the "bin" folder (if asked to override say yes)
4. Make .bat/.sh file with `srcds -game <game name> -ip 0.0.0.0 -console -maxplayers 32 +hostname "SPMP Dedicated Server"` (Replace "&#60;game name&#62;" with the directory name of the game you want)
5. Launch the script

{{TODO|Make this easier for stupid people?}}

