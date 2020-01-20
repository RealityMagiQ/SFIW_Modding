# SpecialForce VR: Infinity War - Mod Editor

## 1. Installation    
### Installation of UE 4.22    
If you haven't installed Unreal Engine 4 yet, download the Unreal Installer from [Epic Games' website](https://www.unrealengine.com/en-US/download).    
In the Epic Game Launcher, download and install 4.22.3 from Unreal Engine-> Library.    
### Installation of the SFIW Mod editor project
Download all the project from this GitHub project and install it in any directory.


## 2. Run
Double click on SpecialForceVR.uproject to launch the editor.

## 3. Create a new Mod
Clicking **Create Mod** in the toolbar at the top of the editor brings up a window where you can create a new Mod directory.    
Enter the appropriate Mod's name in Mod creation window and press **Create Mod** button to complete creation.    
This creates a new plug-in folder with a name added to the Create Mod window with a random string suffix. The name should not overlap with other users' mods, so we recommend that you do not change the generated name as simply as possible.

## 4. Mod Settings
Inside the created directory, an asset named *< Mod name >_Settings* is automatically created.
This asset contains various properties of Steam Workshop items, as well as settings for content of the mod.
* Language: Specifies the language for the text of Steam Workshop items.
* Title: Title of the show at Steam Workshop
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
Create a new map in the mod folder, or copy an external map to it.    
Register the information of the produced map in the Maps item of the Settings asset we saw in the section 4 above.   
Maps for Mod cannot be tested in the editor. See the section 7 for test methods.

## 6. Cooking of a Mod
Click the Steam Workshop icon in the toolbar at the top of the editor to bring up the Workshop management window.    
You can select the Mod to be cooked by choosing on in **Target Mod**, and you can check and modify the Settings asset of the selected Mod by pressing **Edit Mod Settings** button.    
Click **Cook** button to start cooking the selected Mod for testing and deployment.

## 7. Testing a Mod
You can test the cooked resources by loading them into the actual game by pressing **Test** button in the Steam Workshop manager window.    
If you press Test after selecting a map, the game will launch and the map is loaded in single player mode.

## 8. Uploading a Mod
Press **Upload** in the Steam Workshop manager window to upload the cooked Mod package to Steam Workshop. Once the upload is complete, you can check the uploaded items on the Steam app's screen and edit various properties.

## 9. Playing with Mods
The players who have subscribed to the uploaded Steam Workshop items can enter PLAY -> Custom in the game's main lobby, create a custom game based on the uploaded Steam Workshop map, and enjoy multiplayer between the players who subscribed to the same item.
