# VillagePeace
Minecraft Vanilla JAR Mod using the [jarmod-buildsystem-2](https://github.com/Earthcomputer/jarmod-buildsystem-2).

This mod only consists of vanilla patches for
- `gamerule disableZombieSiege`
- Multiplayer: one player sleeping sufficient to set daytime

Updated for Minecraft 1.15.2

There are binary [release zip files](https://github.com/bopindux/VillagePeace/releases) which are installed the 
old fashioned way with your favorite zip tool. 

Unfortunately I still dont understand fabric/mixins well enough to 
replace the jarmod patches with a fabric mod using mixins.  

Note 1: To play on multiplayer, the mod only needs to be installed on the server. 
Vanilla clients can connect, gamerules and multiplayer sleep works only through the server.

Note 2: The mod now with 1.15.2 is so minimal, that the patches can even be applied 
after installing Optifine (tested with preview_OptiFine_1.15.2_HD_U_G1_pre9).

## Why this mod

#### Starting with 1.14.2
When Minecraft 1.14 came out I wanted to use the new features (blocks!) on my old map, 
but didnt want my village getting destroyed or having to fight against illager patrols around my base.
So I created this mod (originally for 1.14.2) to get peace for my village with additional gamerules: 
- `gamerule disableRaids`
- `gamerule disableIllagerPatrols`

Further I fixed the zombie sieges so they actually take place (for 1.14.2) and added a gamerule to turn sieges off:
- `gamerule disableZombieSiege`

Finally I added  'one player sleeping on multiplayer servers'. 
All are very simple fixes - see the patches directory. This mod only consists of patches. 

And hey, now I could play 1.14 on my old map without getting my villagers killed!

#### 1.14.3
With 1.14.3 the `gamerule disableRaids` became part of vanilla and the zombie siege was fixed. So the mod for 1.14.3 
even smaller and only adds gamerules to disable illager patrols and zombie sieges 
as well as the multiplayer sleep patch. 

#### 1.15.2
With 1.15.2 the `gamerule disableIllagerPatrols` became obsolete too, as the vanilla game now has the equivalent `gamerule doPatrolSpawning`.
This time Mojang used a different name to the name I had in 1.14.3, so `gamerule disableIllagerPatrols true` becomes  
`gamerule doPatrolSpawning false`. 

Now the mod only consists of `gamerule disableZombieSiege` and one player sleeping on multiplayer.

Hey, with time, this mod might become completely obsolete...



## Requirements to build
For details on the buildsystem see [jarmod-buildsystem-2](https://github.com/Earthcomputer/jarmod-buildsystem-2) by EarthComputer.

- You need to have at least JDK8 update 92 for recompilation to work, due to a bug in earlier versions of `javac`. 
You also cannot use JDK9 or JDK10 yet.
- Intellij IDEA: import as gradle project
- Run gradle task `setup` in Intellij or `gradlew setup` from command line

### For development
Gradle tasks: `genPatches` (after you change code), `runClient`, `runServer`
    
### To build release
Run gradle task `createRelease` to create zip files in `build/distributions` with classes ready to be dropped into vanilla jars.

## Installation
Just as for any other jar mod. 
- Copy content of [release zip files](https://github.com/bopindux/VillagePeace/releases) to 
vanilla client or server jar (e.g. using 7-zip) and for the client jar remove the folder `META-INF`. 
You can find the vanilla client jar in your `.minecraft/versions` directory.
- Run client jar from launcher: 
  - Create a new Minecraft version for the launcher by copying the client jar to a 
new folder in your `.minecraft/versions` and rename to `1.15.2_VillagePeace.jar`. Thats your vanilla jar.
  - Optifine: the mod for 1.15.2 seems to be compatible to Optifine. So instead of the vanilla jar, you can
  use the jar in your 1.15.2-Optfine version (tested with preview_OptiFine_1.15.2_HD_U_G1_pre9). 
  - Name the folder like the client jar (1.15.2_VillagePeace).  
  - Add the .json file from the vanilla version and and rename like folder (1.15.2_VillagePeace.json).
    - Modify the `id` to "id": `"1.15.2_VillagePeace"` 
    - Empty the 'download' tag in the json to avoid that the vanilla client jar is re-downloaded.
    Note, there are multiple download tags, only empty the one for client, server, mappings download.
    See the example json in the releases. The json for 1.15.2 is for the new launcher.  
  - Alternatively you can take the json file from the release zip.  
  - Create a new profile in the launcher using the new version 1.15.2_VillagePeace.
- Run server jar same as for vanilla jar.
