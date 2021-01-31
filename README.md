## Please look in the branches to see all games available so far for SteamCMD - also the Master branch is suitable for multiple games CS:Source, CS:GO,...


# SteamCMD in Docker optimized for Unraid
This Docker will download and install SteamCMD. It will also install Counter-Strike: Source and run it. Update Notice: Simply restart the container if a newer version of the game is available.

## Env params
| Name | Value | Example |
| --- | --- | --- |
| STEAMCMD_DIR | Folder for SteamCMD | /serverdata/steamcmd |
| SERVER_DIR | Folder for gamefile | /serverdata/serverfiles |
| GAME_ID | SteamID for server | 232330 |
| GAME_NAME | SRCDS gamename | cstrike |
| GAME_PARAMS | Values to start the server | -secure +maxplayers 32 +map de_dust2 |
| UID | User Identifier | 99 |
| GID | Group Identifier | 100 |
| GAME_PORT | Port the server will be running on | 27015 |
| VALIDATE | Validates the game data | true |
| USERNAME | Leave blank for anonymous login | blank |
| PASSWRD | Leave blank for anonymous login | blank |

***ATTENTION: You have to disable Steam Guard for games that require authentication, Steam recommends to create a seperate account for dedicated servers***

>**NOTE** GAME_ID values can be found [here](https://developer.valvesoftware.com/wiki/Dedicated_Servers_List)

> And for GAME_NAME there is no list, so a quick search should give you the result

## Run example
```
docker run --name CSSource -d \
	-p 27015:27015 -p 27015:27015/udp \
	--env 'GAME_ID=232330' \
	--env 'GAME_NAME=cstrike' \
	--env 'GAME_PORT=27015' \
	--env 'GAME_PARAMS=-secure +maxplayers 32 +map de_dust2' \
	--env 'UID=99' \
	--env 'GID=100' \
	--volume /mnt/user/appdata/steamcmd:/serverdata/steamcmd \
	--volume /mnt/user/appdata/cstrikesource:/serverdata/serverfiles \
	ich777/steamcmd:latest
```
>**NOTE** port 26900 is the port for vac, in case of multiple servers make sure these are not the same


This Docker was mainly edited for better use with Unraid, if you don't use Unraid you should definitely try it!


This Docker is forked from mattieserver, thank you for this wonderfull Docker.


#### Support Thread: https://forums.unraid.net/topic/79530-support-ich777-gameserver-dockers/
