# BCI-Unity-Setup-EpochPlus
Start to End Walk-through of Procedure to set up BCI Epoch Plus to connect to Unity interface

# Preparation of BCI headset 
1. Make sure Epoch+ headset is charged. 
2. Clean the metal connector parts of the 16 electrodes.
3. Generously drip saline solution onto sponge surface of electrodes until they are visibly wet (7<drops)
4. Use fingers to screw in the electrodes to the connections on the Epoch+ headset

# Software Preparation (Emotiv App, EmotivBCI (free;without license for Raw EEG signals))
1. Download EmotivBCI and EmotivApp and create an Emotiv account on https://www.emotiv.com/
2. On https://www.emotiv.com/, click 'My Account' (top right), select 'Cortex Apps'
3. Create new cortex app (leave the 'My App requires EEG access' box unchecked if you don't have a license for Raw EEG signals(e.g. EmotivBCI) 
(Note: EmotivPro has license for Raw EEG signals))
4. Save the client secret and client id generated in a note
5. 
Open Config.cs file and insert the saved client secret and client id (step 4) as the elements in the corresponding labels.

In https://www.websocket.org/echo.html, input wss://localhost:6868 to the location field; 
(Communicate with the Cortex API using the WebSocket Secure protocol. according to instructions stated in https://emotiv.gitbook.io/cortex-api/connecting-to-the-cortex-api)
Follow instructions stated in https://emotiv.gitbook.io/cortex-api/overview-of-api-flow 
- in step 7: Call the authorize API to get a Cortex token for subsequence requests, save the Cortex Token generated in a note. 


# Connection to Unity

