include .env

COM_MOJANG=$(LOCAL_APP_DATA)/Packages/Microsoft.MinecraftUWP_8wekyb3d8bbwe/LocalState/games/com.mojang
PROJECT_NAME=My_RESOURCE_Pack

all:

install: My_RESOURCE_Pack
	cp -r $(PROJECT_NAME) $(COM_MOJANG)/development_resource_packs

uuidgen:
	uuidgen
