# SteamCMD in Docker optimized for Unraid
This Docker will download and install SteamCMD. It will also install Counter-Strike: Source and run it. Update Notice: Simply restart the container if a newer version of the game is available.

## Env params
| Name | Value | Example |
| --- | --- | --- |
| STEAMCMD_DIR | Folder for SteamCMD | /serverdata/steamcmd |
| SERVER_DIR | Folder for gamefile | /serverdata/serverfiles |
| GAME_ID | The GAME_ID that the container downloads at startup. If you want to install a static or beta version of the game change the value to: '629800 -beta YOURBRANCH' (without quotes, replace YOURBRANCH with the branch or version you want to install). | 629800 |
| GAME_PARAMS | Values to start the server | empty |
| UID | User Identifier | 99 |
| GID | Group Identifier | 100 |
| GAME_PORT | Port the server will be running on | 7777 |
| QUERY_PORT | UDP Queryport | 27015 |
| BEACON_PORT | UDP Beaconport | 15000 |
| VALIDATE | Validates the game data | blank |
| USERNAME | Leave blank for anonymous login | blank |
| PASSWRD | Leave blank for anonymous login | blank |

## Run example
```
docker run --name Mordhau -d \
	-p 7777:7777/udp -p 27015:27015/udp -p 15000:15000/udp \
	--env 'GAME_ID=629800' \
	--env 'GAME_PORT=7777' \
	--env 'QUERY_PORT=27015' \
	--env 'BEACON_PORT=15000' \
	--env 'UID=99' \
	--env 'GID=100' \
	--volume /path/to/steamcmd:/serverdata/steamcmd \
	--volume /path/to/mordhau:/serverdata/serverfiles \
	ich777/steamcmd:mordhau
```

This Docker was mainly edited for better use with Unraid, if you don't use Unraid you should definitely try it!

This Docker is forked from mattieserver, thank you for this wonderfull Docker.

### Support Thread: https://forums.unraid.net/topic/79530-support-ich777-gameserver-dockers/