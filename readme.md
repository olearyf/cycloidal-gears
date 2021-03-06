# Cycloidal Gear Generator for Fusion 360
### _**Note that this project is a current work in progress, and that this is V1.**_

This is an [Autodesk Fusion 360](http://fusion360.autodesk.com/) add-in for generating cycloidal gears.  Given the input parameters, it will create 3 bodies in a new sketch: cycloidal disk, base plate, and cam.
Example Cycloidal Gear             |  Script Menu
:-------------------------:|:-------------------------:
![](https://github.com/olearyf/cycloidal-gears/blob/main/resources/diskExample.PNG)  |  ![](https://github.com/olearyf/cycloidal-gears/blob/main/resources/scriptExample.PNG)
## Installation

This portion on how to install a script was copied from the wonderful [Voronoi Diagram Generator for Fusion 360](https://github.com/hanskellner/Fusion360Voronoi).

Installing the add-in in the Fusion 360 Addins folder allows it to automatically be found and displayed in the add-ins list.

### Mac Add-Ins Folder

```
"$HOME/Library/Application Support/Autodesk/Autodesk Fusion 360/API/AddIns/"
```

### Windows Add-Ins Folder

```
"C:\Users\%YOUR_USER_NAME%\AppData\Roaming\Autodesk\Autodesk Fusion 360\API\AddIns"
```

1. With your Finder or File Explorer window, locate the AddIns folder.
1. Create a folder within the AddIns folder with the same name as the add-in.  In this case, "CycloidalGear".
1. Extract all of the add-in files from the (ZIP) archive and place them in this folder.
1. Now the add-in is ready for Fusion 360.  Start Fusion 360.
1. Display the Scripts and Add-Ins dialog.  The "CycloidalGear" add-in should be listed.
1. See the *Usage* section below for running and using.

> As an alternative to the above installation location, you can just place the files in their own folder within a location of your choice.  For example, in your Documents or Home folder.  Doing this means the add-in will not automatically appear in the add-ins list.  You will need to manually add it using the "+" button at the top of the list.

There is additional installation help on the Fusion 360 site:

https://knowledge.autodesk.com/support/fusion-360/troubleshooting/caas/sfdcarticles/sfdcarticles/How-to-install-an-ADD-IN-and-Script-in-Fusion-360.html

## Usage
To use the cycloidal gear script, you simply run the script and enter in the values for your parameters, and hit 'OK'. In a new project, the cycloidal disk, base with pins, and cam will be made as 3 separate bodies, along with their corresponding sketches. 

Below is a description of the 9 input parameters:

 - Pin Diameter: This specifies the diameter of the pins along the outer edge of the base. In the example, it is set to a diameter of 0.5 cm. This item takes a double, and it will be parsed in units of centimeters.
![](https://github.com/olearyf/cycloidal-gears/blob/main/resources/Images/pinDiameter.PNG)
 - Number of Pins: This specifies the number of lobes that appear on the cycloidal disk. As an aside, the number of pins that appear on the base is 1 plus what ever number is entered here, so it will likely be renamed in the future. The important thing to note about this input parameter is that it corresponds to your gear reduction. For example, the default value is 10, so a reduction of 10:1 will be achieved. This item takes a double, but note that it will be **truncated** to an integer by the program.
 ![](https://github.com/olearyf/cycloidal-gears/blob/main/resources/Images/pinNum1.PNG)
 ![](https://github.com/olearyf/cycloidal-gears/blob/main/resources/Images/pinNum2.PNG)
 - Cam Radius: This, as you might have guessed, specifies the radius of the cam, or as some refer to it, the eccentric bearing. Note that the value input into this parameter will be offset by the cam tolerance you specify in a later step. So for the default inputs, the radius is set to 1.00 cm, but in the generated body it will have a radius of 1.00 - 0.05(cam tolerance) = 0.95 cm. This item takes a double, and it will be parsed in units of centimeters.
 ![](https://github.com/olearyf/cycloidal-gears/blob/main/resources/Images/camRadius.PNG)
 - Center Pin Radius: This specifies the radius of the center pin, which is attached to the base. It accepts a double that is considered to be in units of centimeters.
 ![](https://github.com/olearyf/cycloidal-gears/blob/main/resources/Images/centerPinRadius.PNG)
 - Cam Tolerance: This is the tolerance specified for the cam. As a result, the outer diameter of the cam is offset by this value, and the eccentric inner hole for the central pin is also offset by this value. It accepts a double and is parsed in units of centimenters.
 - Base Height: Specifies the height of the base plate. It accepts a double and is parsed in units of centimenters.
 ![](https://github.com/olearyf/cycloidal-gears/blob/main/resources/Images/baseHeight.PNG)
 - Pin Height: Specifies the height of the pins and center pin that are attached to the base plate. It accepts a double and is parsed in units of centimenters.
 ![](https://github.com/olearyf/cycloidal-gears/blob/main/resources/Images/pinHeight.PNG)
 - Cam Height: Specifies the height of the cam or eccentric bearing. It accepts a double and is parsed in units of centimenters.
 ![](https://github.com/olearyf/cycloidal-gears/blob/main/resources/Images/camHeight.PNG)
 - Disk Height: Specifies the height of the cycloidal disk. It accepts a double and is parsed in units of centimenters.
 ![](https://github.com/olearyf/cycloidal-gears/blob/main/resources/Images/diskHeight.PNG)

 Below are images of the 3 distinct bodies that are generated by the script:
 ![](https://github.com/olearyf/cycloidal-gears/blob/main/resources/Images/diskBody.PNG)
 ![](https://github.com/olearyf/cycloidal-gears/blob/main/resources/Images/baseBody.PNG)
 ![](https://github.com/olearyf/cycloidal-gears/blob/main/resources/Images/camBody.PNG)

 Below are the 3 sketches generated by the script:
 ![](https://github.com/olearyf/cycloidal-gears/blob/main/resources/Images/diskSketch.PNG)
 ![](https://github.com/olearyf/cycloidal-gears/blob/main/resources/Images/baseSketch.PNG)
 ![](https://github.com/olearyf/cycloidal-gears/blob/main/resources/Images/camSketch.PNG)

## Example
Within the **Example** folder above, you can find a Fusion 360 file that contains a cycloidal gear setup that was generated by the script. In addition to this, are also the 3 STL files the script generates, so you can use them as test prints. The tolerances are set to 0.5 mm, which is optimal for when I printed it on my CR-10. Below is an image of the resulting 3D print, as well as the workspace in Fusion that is generated:
Separate Parts             |  Assembled
:-------------------------:|:-------------------------:
![](https://github.com/olearyf/cycloidal-gears/blob/main/resources/Images/parts.jpg)  |  ![](https://github.com/olearyf/cycloidal-gears/blob/main/resources/Images/assembled.jpg)

![](https://github.com/olearyf/cycloidal-gears/blob/main/resources/Images/exampleResult.PNG)

## About Cycloidal Gears
*Why go cycloidal?* I'm glad you asked!

Cycloidal gears are neat in my book not only because of their looks, but also because of the way they work. Normal gears with teeth are quite easy to understand intuitively, but the first time you look at a cycloidal gear it might be hard to see how it achieves the reduction it does. Essentially, they represent a drastic reduction in revolutions and increase in torque in a pretty compact package.

One common application of cycloidal gears and drives is in robotics. This is because with normal gears(of the involute variety), they have a tendency to slip. So, as you can imagine, if you're controlling a robot and you tell it to go forward 1 meter but due to gear slipping in your gearbox it only goes forward 0.98 meters, you might be in a pickle depending on your application. Because of the geometry of cycloidal gears, this is less of a concern. So, if you use cycloidal gearing in robotics you not only have a great amount of torque to surmount obstacles, but can finely tune your movements.

## TODO

- validate user inputs (ie if a cam radius is too large for a given design, alert the user)
- perform robustness tests
- make a script to create a cycloidal drive
- recognize the units the user is using and be able to switch between metric and imperial units
- more COMING SOON

## Resources

Below are some resources I found helpful in the making of this script, as well as some cool project videos from others who have made cycloidal drives:

 - [3D Printed Cycloidal Gearbox - Solar Rover #2](https://www.youtube.com/watch?v=Ur2eBNMfZIA)
 - [How to Design a Cycloidal Disk in Fusion 360](https://www.youtube.com/watch?v=jQ6LQBFZXmU)
 - [3D printed cycloidal gearbox build and tolerance](https://www.youtube.com/watch?v=Ra8FxDiuQns)
 - [design a cycloidal gear step by step](https://www.youtube.com/watch?v=guvatctnjww)
 - [SolidWorks Tutorial #305 : Cycloidal drive](https://www.youtube.com/watch?v=yIpnEZ_rjZY)
 - [On the lobe profile design in a cycloid reducer using
instant velocity center
](https://ww3.cad.de/foren/ubb/uploads/Clayton/lobe_profile_design_cycloid_reducer.pdf)
 - [Autodesk Fusion 360 API](https://autodeskfusion360.github.io/)
  - [Geometry of Cycloidal Gears](https://www.tec-science.com/mechanical-power-transmission/cycloidal-gear/geometry-of-cycloidal-gears/)
  - [Building a Cycloidal Drive with
SOLIDWORKS
](https://blogs.solidworks.com/teacher/wp-content/uploads/sites/3/Building-a-Cycloidal-Drive-with-SOLIDWORKS.pdf)

## Contact
If you have any questions, notice any bugs, or have any ideas for improvement feel free to contact me at [olearyf@purdue.edu](mailto:olearyf@purdue.edu).
