# G-Code-Flow-Temperature-Controller
A Post Processing Script for Slic3r based Slicers and Klipper Printers.  
  
This 3D Printing Concept is Based on my personal approach and with a minimum of Delphi programming skills.

This Script is free and open source, created to prove the effectiveness of automatic nozzle temperature change during 3D printing in order to get the best Quality/Speed Optimization, but it is not intended to be a definitive solution as I believe that integrating this concept in slicers will be more effective.  
Hoping to soon find this concept in current slicers, because I think this will be the future of 3D printing.  
# Operation and Instructions
Note that [Klipper_Estimator](https://github.com/Annex-Engineering/klipper_estimator) Script is required for time estimation using Klipper Look-Ahead kinematics, and must be in the same Folder with this Script (Included Klipper_Estimator.exe V 3.7.3).  
  
The script operation consists of varying the temperature according to the average flow rate during printing time, then limit the speed in the G-Code to feat the recommended flow rate for the reached temperature.  

The script is located in the Bin folder and can be used as a normal program by opening the SB53-Systems.exe file and opening a GCode manually, or by adding it as a post-processing script in the Slicer.  
  
It is also recommended to add in the slicer Klipper_Estimator.exe path after this script to rewrite the new estimated time into the G-Code.  
```
D:\SB53_G-Code_Flow_Temperature_Controller_V1.0\SB53-Systems.exe;
D:\SB53_G-Code_Flow_Temperature_Controller_V1.0\Klipper_Estimator.exe --config_file D:\SB53_G-Code_Flow_Temperature_Controller_V1.0\config.json post-process;
```
  
![image](https://github.com/user-attachments/assets/a08ed4f5-a5f7-47dd-88eb-09a183e43a2d)  

  
Note that the Slicer Profil must be set for Max Speed, Max temperature and Flow Rate, to have a best Speed/Quality Optemization.  
  
The script will open once the G-Code is generated by the Slicer and ask the user whether the script will be applied or not.   
  
![image](https://github.com/user-attachments/assets/18cf9c84-7255-4cd0-8e8b-ee8856020eae)  
  
If yes:  
  
![Capture](https://github.com/user-attachments/assets/ebb928d5-6a1b-440d-b015-844194574d4c)  
  
The Filament Type and these specific parameters are chosen automatically by the script if (PLA, PETG, ABS, TPU, ASA, HIPS), You need to set the appropriate values ​​according to your extruder limit, then save the changes for next uses.  
You need to refresh the view if you make changes in the the script before generating the G-Code, then Save and Close.  

Below Generated G-Code  
  
![Capture2](https://github.com/user-attachments/assets/c99558b2-5850-4dbd-9020-52db96d0374a)  
![image](https://github.com/user-attachments/assets/83b86611-f5b0-4b45-83f4-ee04094a3d15)  

Next one with Rectilinear sparse infill  
  
![image](https://github.com/user-attachments/assets/c935355b-4272-44d5-aad6-d4083b3f95e4)  
![image](https://github.com/user-attachments/assets/32a0c788-7bfe-4155-bcd3-e7fdd51d3a48)  
  
Take into account that this script is supposed to work under certain conditions :
- Does not accept G2 and G3 in G-Code.
- Time Estimation is based in Klipper Look-ahead kinematics (may not be compatible with Marlin or Others).
- Reading or generating large G-Code files with this Script can takes up to 2 minutes, depending in your CPU.
- Generated G-Code are 30% to 80% larger than the original one due to Temp and Speed adjustment (can be optimized).
- Changing the initial layer temperature is important, and cannot be done in different print start macro, this macro must be in the form below  
  PRINT_START instructions EXTRUDER_TEMP=!!! ... next instructions
  ```
  PRINT_START EXTRUDER_TEMP=[nozzle_temperature_initial_layer] BED_TEMP=[bed_temperature_initial_layer_single]
  ```
  ![image](https://github.com/user-attachments/assets/5e462ac4-0c8b-4537-a21a-f2a1f85b4126)  
  Or  
  ![image](https://github.com/user-attachments/assets/9e6ce605-e440-43f7-b222-e4b80bbe9e1c)  
- This Script is currently only available for windows os.
  
Be responsible and careful with this Script by using reasonable values ​​and monitoring the behavior of your printer, and Happy Smart 3D Printing...  

# Latest Release : 
[SB53 G-Code Flow/Temperature Controller V1.0 (3 Aug 2024)](https://github.com/sb53systems/G-Code-Flow-Temperature-Controller/releases/tag/V1.0)  
  
# About the Developer :
By Salim BELAYEL.  
Developed in June 2024 with Delphi 12 Community Edition.  
Email : sb53systems@gmail.com  

![SB53-Systems~1](https://github.com/sb53systems/G-Code-Flow-Temperature-Controller/assets/33290411/b94703a1-cf21-4109-bfa6-b9bcff438a1d)  

  
If you find my work worthy, Bay me a coffee. Thank you.  
  
[![image](https://github.com/sb53systems/G-Code-Flow-Temperature-Controller/assets/33290411/a504ac44-082d-40f1-a9d0-4abc3da242d8)](https://ko-fi.com/sb53systems)
 [Co-fi](https://ko-fi.com/sb53systems) 


