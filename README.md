# VillagePeace
Minecraft Vanilla JAR Mod using the [jarmod-buildsystem-2](https://github.com/Earthcomputer/jarmod-buildsystem-2).

This mod only consists of vanilla patches for
- `gamerule disableIllagerPatrols`
- `gamerule disableZombieSiege`
- Multiplayer: one player sleeping sufficient to set daytime

Updated for Minecraft 1.14.3 (`gamerule disableRaids` now part of vanilla).

## Why this mod
When Minecraft 1.14 came out I wanted to use the new features (blocks!) on my old map, 
but didnt want my village getting destroyed or having to fight against illager patrols around my base.
While raids where possible to be disabled with the pre-release of 1.14.3, zombie sieges came back instead.

So I went ahead with 1.14.2 (the latest the build system was available for) and added the gamerules to get peace for my village. 
I also fixed the zombie siege for 1.14.2, so when not disabled, they actually take place as in 1.14.3 pre release.
And hey, now I can play 1.14 on my old map without getting my villagers killed!

With 1.14.3 the mod is even smaller and only adds gamerules to disable illager patrols and zombie sieges 
as well as the multiplayer sleep patch. 

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
new folder in your `.minecraft/versions` and rename to `1.14.3-VillagePeace.jar`.  
  - Name the folder like the client jar (1.14.3-VillagePeace).  
  - Add the .json file from the vanilla version and and rename like folder (1.14.3-VillagePeace.json).
    - Modify the `id` to "id": `"1.14.3-VillagePeace"` 
    - Empty the 'download' tag in the json to avoid that the vanilla client jar is re-downloaded.  
  - Alternatively you can take the json file from the release zip.  
  - Create a new profile in the launcher using the new version 1.14.3-VillagePeace.
- Run server jar same as for vanilla jar.
