# MJM_BlenderFBX_ScrapMechanic_Mod

Modified FBX Export script for Blender2.8

I have added custom bone axis correction matrix for correcting the angle of character steering animations in the game ScrapMechanic.
My added code in the python files is tagged with the comment 'MJM ScrapMechanic Mod'.

![](images/Screenshot.png)

Issue I'm addressing: 
When making custom driverseat models, the character's steering animation is located at a bone named "j_root" in your seat model, and the tilt angle of the steering animation is usually aligned to a bone named "j_ratt". However, when using FBX models instead of Ogre.mesh, the angle of the j_ratt bone seems to be ignored. 
I have found a solution by changing the Primary Bone Axis upon export, which is affecting the angle of the character steering animation while not affecting the baked animation of the seat model. But the FBX Exporter only allows for axis changes such as X, Y, Z, and not arbitrary angles.
To address this I have added the ability to use a bone correction matrix with angles from 0 - 90.

To use:
1: Copy the files '__init__.py' and 'export_fbx_bin.py' into the script folder for the FBX Exporter '...\Blender Foundation\Blender 2.81\2.81\scripts\addons\io_scene_fbx'.

2: When exporting to FBX, check the box 'ScrapMechanic Driverseat?' and enter the tilt angle of your steering wheel in the box 'Steering Tilt Angle'. 
The minimum value of 0 is a straight horizontal steering (car-like), and the maximum value 90 is a straight vertical steering (motorcycle-like). I didn't allow values that are negative or greater than 90 as they don't make sense for a reasonable steeringwheel tilt.

Note: This all applies to a seat model in the correct orientation for Scrap Mechanic seats. 
The top of the seat must face the +Y direction, and the front of the seat must face the +Z direction. 
Although the world in Scrap Mechanic is Y forward, Z up, the seated character pose uses Z forward, Y up orientation.


