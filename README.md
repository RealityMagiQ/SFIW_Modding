# SpecialForce VR: Infinity War - Mod Editor

## 1. Installation    
### Installation of UE 4.22    
If you haven't installed Unreal Engine 4 yet, download the Unreal Installer from [Epic Games' website](https://www.unrealengine.com/en-US/download).    
In the Epic Game Launcher, download and install 4.22.3 from Unreal Engine-> Library.    
### Installation of the SFIW Mod editor project
Download all the project from this GitHub project and install it in any directory.

## 2. Running the SFIW Mod editor
Double click on SpecialForceVR.uproject to launch the editor.    
Note that you must be logged in to Steam before launching the editor.

## 3. Create a new Mod
Clicking **Create Mod** in the toolbar at the top of the editor brings up a window where you can create a new Mod directory.    
![toolbar](https://user-images.githubusercontent.com/57106512/72774434-f80d7000-3c4d-11ea-9ad1-3bbc8066c575.jpg)   
Enter the appropriate Mod's name in Mod creation window and press **Create Mod** button to complete creation.    
![CreateMod](https://user-images.githubusercontent.com/57106512/72774518-415dbf80-3c4e-11ea-9b78-9f1235f82672.jpg)   
This creates a new plug-in folder with a name added to the Create Mod window with a random string suffix. The name should not overlap with other users' mods, so we recommend that you do not change the generated name as simply as possible.

## 4. Mod Settings
An asset named *< Mod name >_Settings* is automatically created inside the created Mod directory.   
![ModContents](https://user-images.githubusercontent.com/57106512/72776220-b7652500-3c54-11ea-842f-a6b94a84d16e.jpg)   
This asset contains various properties of Steam Workshop items, as well as settings for content of the mod.   
![ModSettings](https://user-images.githubusercontent.com/57106512/72776532-dd3ef980-3c55-11ea-92a6-59c6dfac9e46.jpg)   
* Language: Specifies the language for the text of Steam Workshop item.
* Title: Title of the item at Steam Workshop
* Description: Description of the item to be displayed in the Steam Workshop.
* Change Note: A change note that will be added to items in the Steam Workshop upon upload.
* Visibility: Visibility of this item in the Steam Workshop
* Preview Image: Thumbnail image of this item to view in Steam Workshop
* Maps: list of maps to be included in this Steam Workshop item
  * Display Name: The name of the map to show to the user
  * Description: A description of the map to be shown to the user.
  * Thumbnail: Thumbnail of the map
  * Max Player: Maximum number of players available
  * Level: Map Resources
  * Game Mode Category: Choose whether the game mode your map supports is individual or team
  * Support AI: AI support in game mode
* Published File Id: ID of this item on the Steam Workshop. If it is empty, it will be automatically assigned on upload.

## 5. Creating a Map
Create a new map in the mod folder, or copy an external map to it. See the section 10 and 11 for the detailed information on actors required for your map to work with SF:IW game.    
Register the information of the produced map in the Maps item of the Settings asset we saw in the section 4 above.   
Maps for Mod cannot be tested in the editor. See the section 7 for test methods.

## 6. Cooking of a Mod
Click the Steam Workshop icon in the toolbar at the top of the editor to bring up the Workshop management window.    
![WorkshopManager](https://user-images.githubusercontent.com/57106512/72776606-22fbc200-3c56-11ea-991c-17da578b1077.jpg)    
You can select the Mod to be cooked by choosing on in **Target Mod**, and you can check and modify the Settings asset of the selected Mod by pressing **Edit Mod Settings** button.    
Click **Cook** button to start cooking the selected Mod for testing and deployment.
![Cooking](https://user-images.githubusercontent.com/57106512/72776728-8554c280-3c56-11ea-9536-78456797336a.jpg)   

## 7. Testing a Mod
You can test the cooked resources by loading them into the actual game by pressing **Test** button in the Steam Workshop manager window.    
If you press Test after selecting a map, the game will launch and the map is loaded in single player mode.

## 8. Uploading a Mod
Press **Upload** in the Steam Workshop manager window to upload the cooked Mod package to Steam Workshop. Once the upload is complete, you can check the uploaded items on the Steam app's window and edit various properties.

## 9. Playing with Mods
The players who have subscribed to the uploaded Steam Workshop items can enter PLAY -> Custom in the game's main lobby, create a custom game based on the uploaded Steam Workshop map, and enjoy multiplayer games between the players who subscribed to the same item.

## 10. Actors for SF:IW maps
### Blueprints   
**BP_SFPlaygroundGameMode**   
 - GameMode for PlayGround (players are invincible, infinite game play time)   

**BP_SFOnlineDMGameMode**   
 - GameMode for DeathMatch   

**BP_SFOnlineTDMGameMode**   
 - GameMode for TeamDeathMatch   

**BP_SFOnlineDemolitionGameMode**   
 - GameMode for DemolitionMatch
 - (P) TotalRound : Number of total rounds for a session. The team which scores more than half of the total rounds wins.

### ModEditor_Blueprint
**BP_SFPlayerStart**
- This actor defines the start and respawn location of players   
* (P) TeamID   
  * -1: this player start is valid for any team   
  * 1: only for the players of team AUA   
  * 2: only for the players of team MAF   
* (P) PlayerID   
  * -1: valid for any player   
  * 0~: Only for a corresponding sequence user. The user sequence increases from 0 for each new player joins.   
  * In case of DemolitionGameMode, there is a special area of waiting room. If you add a tag called “WaitRoom” to ActorTag, it is determined as starting point in the waiting room.

**BP_SF_AllAmmo_Spawner**   
Ammo Supply Box. Place it at your desired location.

**BP_SF_DemolitionPoint_Spawner**   
(DemolitionMode Only / Experimental) Specify the bomb installation location.   
After the object is placed on the map, the location or size of the components should be specified according to the terrain.
* (P) Side: Either of A, B, C can be specified
* (C) SetupZone: Bomb installation area
* (C) AreaZone: The area where TootipUI and the bomb hologram are visible
* (C) BombAttachPoint: The location to attach to a bomb. (please check the direction and size with C4GuideMesh and Arrow)
* (C) Camera: When the attacking team completes the bomb installation and the power is dead, it will be displayed on the screen.
* (C) BombSetupUI: Applies installation location UI, position and rotation only (ignores Scale)
* (C) BombTooltipUI: Installation instructions UI, only apply position and rotation (ignore Scale)

**BP_SF_DemolitionSpectatorScreen_Spawner**   
It represens a screen in Waiting Room. It shows alive players for dead players in Waiting Room.   
Since the actor is not scaled, only the position and rotation need to be modified.   
* (P) IsOffenceTeam: True if this spawner is for the attacking team
Note that team 2 is the attacking team in the first round. This should be set accordingly in the Waiting Room.
  
## 11. Sample Maps
You can see the sample maps provided under Mods/Example_777583B24412 from the downloaded Mod editor project.
### ODM_Example
A sample map for the Deathmatch game mode.
### ODML_Example
A sample map for the Demolition game mode.
### OTDM_Example
A sample map for the Team Deathmatch game mode.
### PlayGround_Example
A sample map for the Playground game mode.

