Don't forget to come join the game's offical discord if you need help or want to release your mod somewhere: https://discord.gg/ballisticng

Browse the game's code base here, updated every major game update: https://vonsnake.gitlab.io/BallisticNG-ModdingReferences/namespaces.html

# Important Stuff
* If you're only installing mods and not developing them, remember that these mods can do anything that a standalone application can and could be potentially dangerous. Only download BallisticNG code mods from reputable and trustworthy sources and favour open source mods that you can inspect yourself whenever possible.
* This repo contains mods that will only work for 1.0 and higher, make sure you're up to date before trying to use them.
* Mods cannot be written for or used in multiplayer, you will need to disable them in order to use multiplayer. You can launch the game with the **-nomods** switch to disable mods without affecting their saved state option.

# For non-developers: Installing mods
Make sure you have a program installed that can open zip files such as 7-zip or Winrar

* Click the green button at the top right of this repo, select **Download ZIP** from the little window that opens
* When downloaded and the .zip is open, drag the folders inside to the **UserData/Mods** folder where BallisticNG is installed
* Launch the game, go to the **Manage Mods** screen under the **Mods** tab and set the mods state to **On**
* Restart the game


# Debugging
If you're using the in-game compiler then you can check for compiling errors using the console. Press Ctrl + Backspace to toggle it, all compiling errors will be printed into this.

Using the **unitylog true** command will hook into Unity's logger and also print out anything output to the Unity log. This can be useful for debugging in-game issues.

# Where do mods go?
All mods go in **%Install_Dir%/UserData/Mods**. Each mod must have its own folder inside of this folder, so for instance the Custom Shield mods path should be **%Install_Dir%/UserData/Mods/Custom Shield**.

Mods can be either the raw .cs files or a precompiled .dll. If a .dll is present the game will load that, if there isn't a .dll present then the game will look for .cs files to compile.

# How do I activate mods?
For security reasons newly installed mods are disabled by default and must be manually activated before use. You can do this from the Manage Mods screen on the menu. Set the state to **on**, restart the game and your mod will be loaded.

If you are letting the game compile your raw .cs files you might also be interested in the **always recompile** option. With this enabled the game will recompile your .cs files every launch, this saves you having to delete the .dll file everytime you make a change to your code.

# Compiling
BallisticNG comes with a built in C# compiler so all you really need to write mods is literally anything that can edit text. However it's reccomended that you use an IDE such a Visual Studio as you'll be able to reference the game's libraries and use intellisense.

If using an IDE to compile then all you need to do is copy the .dll you compile into your mods folder and the game will load it on launch.

**Note**: the in-game compiler is using an older .net 3.5 based version of Mono, if you want to take advantage of newer C# features then you'll want to compiled your own .dll.

# Set up IDE references
All of the libraries you want to reference can be found in **%Install_Dir/BallisticNG_Data/Managed**. The files you want to reference are:

* Assembly-CSharp.dll (this is the core of the game)
* BallisticModding.dll (mod file formats)
* BallisticSource.dll (contains the mod register you need. I know, should really be in BallisticModding)
* BallisticUI.dll (not really important, used primarily for the in-game mod tool UIs)
* BallisticUnityTools.dll (if you want to work with custom tracks)
* Any DLL containing **UnityEngine** (these are Unity's libraries, you must reference these)
