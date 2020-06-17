## MisModding-101
A Miscreated Modding guide for beginners.
*Created by the Miscreated Modding community and put together by 4iY* 
## Introduction 
So, you’ve seen all these fancy mods on the Steam Workshop and want to do the same (or at least come close to them)? You have come to the very right place then – this guide will teach you in detail how to create mods. It’s divided into sections for your convenience.
## Sections
- Initial set-up
- Mod flow, uploading to Steam + Examples
- Extras (manual mod upload)

## Initial Set-up
Making mods takes some initial set-up steps to be done. I recommend creating an empty folder somewhere (preferably on a drive that has a bit of free space) where the modding files will be put in. Now let’s dive straight into it.

1.1) Download the files to upload the mod (we’ll do that part a bit later, after we actually create the modification) from this video’s description (official link provided by the developers): https://www.youtube.com/watch?v=Ucqr21oA0WY

1.2) Download Theros’s MisModPacker under this link: https://github.com/4iY/MisModPacker  and save it in a separate folder (it will be used a lot)

1.3.1) Install SteamCMD from this official link (put it in a separate folder but remember where it is): https://steamcdn-a.akamaihd.net/client/installer/steamcmd.zip

1.3.2) Alternatively, you can use a 3rd-party tool created by Theros to upload mods - all instructions for its usage and the link to download it is in here: https://svaltek.gitlab.io/projects/mismodpublisher/ . Using this particular application is beyond the scope of this guide.

1.4) It is also recommended to install Notepad++ for editing LUA and XML files for modding (https://notepad-plus-plus.org/downloads/ ) and an archiving software. There is one personally recommended by experienced modders – PeaZip (https://www.peazip.org/), but you can use the likes of WinRar or 7zip if you want to assuming they do not cause issues with your system.

### WARNING!
**Never edit any file directly** – instead, copy it somewhere separate from the game, such as your Desktop, and make all changes there. Directly editing files, especially inside the game’s GameSDK folder, is a sure way to data corruption.

## Examples and Modding Flow
The easiest part of modding is what I call re-scripting, such as changing spawn values or percentages, yet is still takes some expertise to do correctly. Let’s take the file called VehicleSpawnerManager.lua (located under Scripts.pak\Scripts\Spawners) as an example here. 

NEEDS DETAIL!

## Making&Uploading a mod
Every mod for Miscreated is in the form of a .pak archive. So how exactly does one create it?
It is trivial – all you have to do is put all files inside the correct folders (you may need to create them – see **warning** below) in the Workspace folder of MisModPacker (which we downloaded previously) and then run CreatePak.bat. You new .pak file will be located in Build called workshop_build.pak - you may rename it.

### WARNING!
There is one very important part here, ***you must retain the folder structure leading to whatever files you want to upload in full.*** Meaning you cannot just upload the few .lua files we adjusted inside a .pak as is. The inner structure of the .pak file has to copy that of the GameSDK and original .pak files: as an example, for the VehicleSpawnerManager.lua file you would need to mimic the folders leading to it, starting with the GameSDK folder. It would look like this: `MyMod.pak\GameSDK\Scripts\Spawners\VehicleSpawnerManager.lua`

### Uploading a mod
After we created the .pak file all that’s left is to upload it, and that is done via the mod_create.bat file. Before we proceed, open the mod.vdf file and edit the Path (*it has to be leading to the .pak file of the created mod*), Title and Description, last two being recommended but entirely optional. 
Now Right-click on the mod_create.bat file and press Edit (you can use any text editor for that). Adjust, if necessary, the path to your SteamCMD installation. Then, replace the login and password words with those of your Steam account.
### NOTICE!
You cannot upload mods from an account that is currently in use, like someone logged in on it. *If you do not have another Steam account kill the process called Steam Client Bootstrapper in Task Manager.* **If your login has a dot or a special symbol then this will not work, there will be an explanation further down how to manually upload mods**) – ***make sure to remove the less than / more than (< and >) symbols but retain all spaces.*** Next, adjust the path to mod.vdf so it leads to where it actually is located. Then save the file and double-click on it to run the .bat. 
Upon doing so a SteamCMD window will pop up – it may ask you to fill in the Steam Guard code, please do so if it does – and the process of uploading the mod should start. If it doesn’t, double-check all paths inside both mod.vdf and your mod_create.bat file. If you cannot figure out what’s going wrong, please jump to Extras for a guide on how to manually use SteamCMD to upload mods.
You will find the ID of your freshly created mod under PublishedFileID inside the mod.vdf file – that is the exact ID which is put in a server’s mod list.

## Extras
### Manual use of SteamCMD to upload mods (if having issues using .bat file)
1) Open SteamCMD.exe directly from its installation

2) Type in **`login USER PASSWORD`** , replacing the last two words with your Steam login credentials and press Enter (enter your Steam Guard code if prompted to)

3) Type **`workshop_build_item THEPATH`** , replacing **THEPATH** with the full path to the mod.vdf file (that’s the same path as you would input into the mod_create.bat file). The uploading process will now start. You can grab the ID of your fresh mod either from the SteamCMD window itself or from the mod.vdf file assuming you cleared the previous ID from there (if it was not there then dont worry).
