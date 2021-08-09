# BCI-Unity-Setup-EpochPlus
Start to End Walk-through of Procedure to set up BCI Epoch Plus to connect to Unity interface. Steps listed are in sequential order.

# Preparation of BCI headset 
1. Make sure Epoch+ headset is charged. (White light indicator near headset switch when 'on')
2. Clean the metal connector parts of the 16 electrodes.
3. Generously drip saline solution onto sponge surface of electrodes until they are visibly wet. (8<drops)
4. Use fingers to screw in the electrodes to the connections on the Epoch+ headset.

# Software Preparation (Emotiv App, EmotivBCI (free;without license for Raw EEG signals))
1. Download EmotivBCI and EmotivApp and create an Emotiv account on https://www.emotiv.com/
2. On https://www.emotiv.com/, click 'My Account' (top right), select 'Cortex Apps'
3. Create new cortex app (leave the 'My App requires EEG access' box unchecked if you don't have a license for Raw EEG signals(e.g. EmotivBCI) 
(Note: EmotivPro has license for Raw EEG signals))
4. Save the client secret and client id generated in a note.

# Calibrating the headset
1. In EmotivBCI, create new profile for yourself to train.
2. Connect BCI headset device. (click Connect button and select the device you wish to connect to)
3. Start training motor sensory/facial expression commands.

# Download Unity Package from: 
https://github.com/BrandlMax/BrainFramework 

Steps: 
1. Navigate to your unity project's packages folder in command prompt.
2. Type: git clone https://github.com/BrandlMax/BrainFramework 
3. Launch Unity Project.
4. Click button at the top left corner: Assets-> Import Package->Custom Package-> select unity package. 
- if encountered error: Deterministic compilation failed. You can disable Deterministic builds in Player Settings,  
- Solution: button at top left corner: Edit->Project Settings->Player->**Use deterministic build** (make sure this option is **unchecked**)
5. Add BrainFramework prefab into Game scene, fill in the websocket url: wss://localhost:6868, the clientSecret, Clientid, Device Name details according to your own details in the respective fields in GameInspector. 
(or edit those fields in BrainFramework script). 
7. Add Ball controller equivalent script to your intended object to control. Drag BrainFramework prefab to relevant field in Ballcontrollerscript in Inspector Panel.

# Additional Requirement
Open Config.cs file and insert the saved client secret and client id (step 4 of software ) as the elements in the relevant corresponding labels. (near the top section of config file)

# Connection to Unity
1. Insert the Emotiv Epoc+ Dongle to a USB port of your computer
2. Ensure that you have closed the EmotivBCI application once you have finished training. (Data streaming in Unity cannot happen until EmotivBCI application is closed)
3. If 'APIs not registered error' is encountered, try: (1) changing the USB port you are using for the Emotiv Epoc+ Dongle. or (2) Restarting your computer or (3) Charging your Emotiv Epoc+ device for a while more before trying the previous 2 steps again. 

**Change profile name in Brainframework script or relevant field when conducting trials for a different user profile.

# Device cleanup
1. If the device surface becomes sticky after storage/usage, use a cotton pad and rubbing alcohol to clean the surface. 
2. Remove the electrodes from the connection points (gently twist to unscrew using fingers), wipe metal parts dry and place them in the case.
3. Dab a tissue/towel on the sponge surfaces to absorb excess saline solution. 
4. Leave the sponges out to dry in the sun.

# Additional Resources
Websocket: In https://www.websocket.org/echo.html, input wss://localhost:6868 to the location field; 
(Communicate with the Cortex API using the WebSocket Secure protocol. according to instructions stated in https://emotiv.gitbook.io/cortex-api/connecting-to-the-cortex-api)
Follow instructions stated in https://emotiv.gitbook.io/cortex-api/overview-of-api-flow 
- In step 7: Call the **authorize** API to get a Cortex token for subsequence requests, save the Cortex Token generated in a note. 
- If encountered error: 'please call authorize() API with a debit number' after calling authorize API, 
- Solution: retry calling authorize API (with ' "debit": 1 ' param after the "clientid" and "clientSecret") (need a number, can be >1)

Personal project reference: https://github.com/solarspaceclouds/Emotiv-BCI-Game-PacGhost
