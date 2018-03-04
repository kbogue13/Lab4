Introduction:

This tutorial will explain how to change the basemap from a drop-down menu. This tutorial will be conducted within the AppStudio for ArcGIS/QTCreator environment. QTCreator is bundled within AppStudio for ArcGIS. 

If you do not have AppStudio for ArcGIS installed you can download it here: http://doc.arcgis.com/en/appstudio/download/. 


How to Change the Basemap:
1.	With AppStudio for ArcGIS open, choose ‘New App’
![alt text](https://github.com/kbogue13/Lab4/blob/master/images/picture1.PNG?raw=true)

2.	A new window will open showing a number of different headings. For this tutorial, we will: A: App option, B: give the app a title and C: click ‘Create’

![alt text](https://github.com/kbogue13/Lab4/blob/master/images/picture2.PNG)

3.	Clicking ‘Create’ in step 2 will bring you back to the home screen where you will see your newly created app. In this example it was named ‘ChangeBasemap’, but yours will reflect the title you chose.
  A: Select your newly created app
  B: Click ‘Edit’ to open your app in QTCreator
![alt text](https://github.com/kbogue13/Lab4/blob/master/images/picture3.PNG?raw=true)

4.	With QTCreator now open, you will see that your applicatoin already contains some code. That is because the Hello World (Runtime) app that we created already contains the code to display a map, find user location and return to a default extent.

      If you would like to create a map from scratch with different functionality, information on how to do so can be found here:                                             https://developers.arcgis.com/qt/latest/qml/sample-code/sample-qt-displaymap.htm
![alt text](https://github.com/kbogue13/Lab4/blob/master/images/picture4.PNG?raw=true)

The code needed to place a drop-down menu to change basemaps is:

ComboBox {
        id: comboBoxBasemap
        anchors {
            left: parent.left
            top: parent.top
            margins: 15 * scaleFactor
        }
        width: 175 * scaleFactor
        model: ["Topographic","Streets","Imagery","Oceans"]
        onCurrentTextChanged: {
            // Call this JavaScript function when the current selection changes
            if (map.loadStatus === Enums.LoadStatusLoaded)
                changeBasemap();
        }

        function changeBasemap() {
            // Determine the selected basemap, create that type, and set the Map's basemap
            switch (comboBoxBasemap.currentText) {
            case "Topographic":
                map.basemap = ArcGISRuntimeEnvironment.createObject("BasemapTopographic");
                break;
            case "Streets":
                map.basemap = ArcGISRuntimeEnvironment.createObject("BasemapStreets");
                break;
            case "Imagery":
                map.basemap = ArcGISRuntimeEnvironment.createObject("BasemapImagery");
                break;
            case "Oceans":
                map.basemap = ArcGISRuntimeEnvironment.createObject("BasemapOceans");
                break;
            default:
                map.basemap = ArcGISRuntimeEnvironment.createObject("BasemapTopographic");
                break;
            }
        }
    }

This block of code needs to be input into the existing code in order to create the basemap drop-down menu.

To do so we will place it within the existing code that contains all the code associated with the map (i.e. the code needed to show a map, the code to for a button that finds the user’s location, etc.)

In QTCreator, within the code scroll down until you see:
![alt text](https://github.com/kbogue13/Lab4/blob/master/images/picture5.png?raw=true)

This is the code that displays the default basemap in your app.

We need to input the basemap drop-down menu code below this code, but above the next section of code:

![alt text](https://github.com/kbogue13/Lab4/blob/master/images/picture6.PNG?raw=true)

When the basemap drop-down menu code is input into the existing code, it should look like this:
![alt text](https://github.com/kbogue13/Lab4/blob/master/images/picture7.PNG?raw=true)

Now it is time to save your work.

To save your work click ‘File’ -> ‘Save MyApp.qml As…’ and choose a name and place where you would like to save.

DO NOT FORGET TO SAVE YOUR WORK!!!

Once your work is saved, you can return to AppStudio for ArcGIS and double click on your app to launch it.

If you have correctly placed the code, the drop-down menu to change the basemap should appear and the app you have created should look like the example below and have a functioning drop-down that changes the basemap.

![alt text](https://github.com/kbogue13/Lab4/blob/master/images/picture9.png?raw=true)

If your app looks like this and the drop-down works, congratulations!

If it does not, go back and make sure you have copied all the code correctly and make sure you have placed it properly.

If all else fails, you may copy/paste all the code to produce the above map and drop-down from:
https://github.com/kbogue13/Lab4/blob/master/code
