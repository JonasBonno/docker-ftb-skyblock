# ftb-skyblock - v2.0.1
Feed The Beast Infinity Evolved Skyblock modpack
made by Feed The Beast at https://feed-the-beast.com

Modpack for Minecraft 1.7.10.
FTB Infinity Evolved Skyblock is a modpack designed to provide an extra challenge for any experienced Minecrafter. Work your way through new recipes, twisted game mechanics, and collect the rare and mysterious trophies! Warning, may consume a vast amount of your time. Fastcraft is enabled in this pack by default.

<img src="http://media-elerium.cursecdn.com/avatars/37/382/635951126086881336.png" width="338" height="338">

NOTE: In compliance with Mojang "End User License Agreement", you will need to agree to the EULA in order to run your own Minecraft server. By using this container you acknowledge the EULA! If you do not agree, then you are not permitted to use this container!
https://account.mojang.com/documents/minecraft_eula

This Dockerfile will always download latest build of Feed The Beast Infinity Evolved when building.
The releases on hub.docker.com are build when a new stable release is available fro Feed The Beast.

The worldname must be the default "world". 
Settings will reset when upgrading.
Access the console to op and whitelist.

Running ftb-infinity data container:
docker run --name [name of your data container] jonasbonno/ftb-skyblock:2.0.1 echo 'Data-only container'

Running ftb-infinity server:
docker run --tty=true --interactive=true --detach=true --name=[name of your container] --volumes-from [name of your data container] --publish=[port on your host]:25565 jonasbonno/ftb-skyblock:2.0.1

Upgrading from v1.1.0 or older: </br>
1 - Shutdown Minecraft container </br>
2 - docker run -it --rm --volumes-from [name of your old data container] -v $(pwd):/backup alpine sh </br>
3 - mkdir /minecraft </br>
4 - cp /opt/minecraft/[name of your world] /minecraft </br>
5 - tar zcpf /backup/[name of your backup file].tgz minecraft/world </br>
6 - Create a new v1.2.0 or newer Minecraft container + data container </br>
7 - Shutdown new Minecraft container when idle </br>
8 - docker run --rm --volumes-from [name of your new data container] alpine rm -rf /minecraft/world/* </br>
9 - docker run --rm --volumes-from [name of your new data container] -v $(pwd):/backup alpine tar zxpvf /backup/[name of your backup file].tgz </br>
10 - docker run --rm --volumes-from [name of your new data container] alpine chown -R 1000:1000 /minecraft </br>
11 - docker run --rm --volumes-from [name of your new data container] alpine chmod -R 755 /minecraft </br>

When upgrading sometime items have been remove and therefor you have to confirm removal. </br>
To do so run "docker attach [name of your container]" and type "/fml confirm" when prompted to confirm or cancel. </br>
Exit with CTRL+P CTRL+Q. </br>

To access the console:
</br>docker attach [name of container]
</br>Run your commands
</br>To exit: CTRL+P CTRL+Q

The first time the server starts it creates the server.properties file with default settings and spawns "world". 
Not recommended to change these settings be hand.

When upgrading:
To upgrade delete ftb-infinity server and start new ftb-infinity server with --volumes-from [name of your data container].
Settings will reset when upgrading.
Access the console to op and whitelist.
