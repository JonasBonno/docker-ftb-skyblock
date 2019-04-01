# ftb-skyblock - v1.1.0
Feed The Beast Infinity Evolved Skyblock modpack
made by Feed The Beast at https://feed-the-beast.com

Modpack for Minecraft 1.7.10.
FTB Infinity Evolved Skyblock is a modpack designed to provide an extra challenge for any experienced Minecrafter. Work your way through new recipes, twisted game mechanics, and collect the rare and mysterious trophies! Warning, may consume a vast amount of your time. Fastcraft is enabled in this pack by default.

<img src="http://media-elerium.cursecdn.com/avatars/37/382/635951126086881336.png" width="338" height="338">

NOTE: In compliance with Mojang "End User License Agreement", you will need to agree to the EULA in order to run your own Minecraft server. By using this container you acknowledge the EULA! If you do not agree, then you are not permitted to use this container!

Running ftb-infinityskyblock:
docker run -d -p 25565:25565 -v [path to data location on host]:/opt/minecraft jonasbonno/ftb-skyblock:1.1.0

To access the console:
</br>docker attach [name of container]
</br>Run your commands
</br>To exit again press CTRL+P and then CTRL+Q

I personaly use:
docker run --tty=true --interactive=true --detach=true --name=CONTAINERNAME --publish=25565:25565 --volume=[path to data location on host]:/opt/minecraft jonasbonno/ftb-skyblock:1.1.0

The first time the server starts it creates the server.properties file with default settings and spawns "world". 
Feel free to modify to your preferences. 

To change the server.properties file:
- Stop the container.
- Modify server.properties in your directory. Use sudo if permission errors.
- If you changed the servername. Delete "world" folder to save some diskspace.

When upgrading:
- Move your "world" folder, server.properties, and e.g. also whitelist.json, ops.json etc to a secure location.
- Delete everthing in [path to data location on host].
- Create new container and let it startup completely the first time.
- Turn it off and copy your folder and files back.
