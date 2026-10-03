---
title: "Lebronite"
author: "Yousif Hassanein"
description: "A short description of your project"
created_at: "2026-10-1"
---

# October 1: Wrote down the overall idea and first thoughts about the project

A drive train that is controlled with hand gestures.

The drive train will have the capabilities to strafe in any direction horizontally. The drivetrain will be programmed to follow a specific action based on the gesture created by the user's two hands. A hand gesture will be made by taking 2 types of data:
- Which fingers are bent and which fingers are not bent
- How fast each hand is moving. An accelerometer will be used to detect the velocity of the hand it is attached two.

The user will wear gloves that will have sensors detecting the nature of the user's fingers and how how fast the hands are moving. These gloves will then connect to the drive train using Wifi Capabilities given by an ESP 32. The drive train will also have an esp 32 module. 

The possible finger bent combinations that are possible are theorized to be 2^10 power. This is because I have 10 Fingers ( thank god) and depending on which fingers are bent and which fingers aren't bent there are this many possible combinations I can use. 

To visualize this, think of Binary and imagine all 10 fingers are assigned a value of either 0 or 1. If the finger is straight then its 0 and if the finger is bent then its 1.

Now imagine my hands are wide open and I'm showing my palms and all 10 fingers are straight. 

![Open Hands Image](Hands%20journal.jpg)

This would be assigned a value of 0,000,0   00,000
*Ignore the commas they are js there so I can properly count 😭

If only my left thumb was closed then the value could be 00001  00000
If the right thumb was closed/bent then the value could be 00000  10000
If the left thumb and right thumb was bent then the value could be 00001  10000
There are 10 placeholders each with a state of 1 or 0. With each placeholder has 2 values it can be. This means 2^10 represents the amounts of values I can create with my fingers which equals 1024. I have 1024 combinations, values, or signals I can make simply using if a finger is bent or straight. However, it becomes a bit difficult to make all those combinations. I will test out the combinations I can make with my hands and see which ones are hard.


Left hand combinations. Should be mirrored to the right as well but for sake of time, I won’t repeat all the test. 
5 Fingers. Gives 2 combinations
1 - All fingers closed
1 - All Fingers open

4 Finger. Gives 4 combinations
1 - Exclude thumb
1 - Exclude index
1 - Exclude Middle
0 - Exclude Ring. Feeling some difficulty and finger is slipping so won’t count for now
1 - Exclude Pinky

3 Fingers. Gives 8 Values
Thumb X Index X Middle
Thumb X Index X Ring
Thumb X Index X Pinky
Thumb X Middle X Ring
Thumb X Middle X Pinky
Thumb X Ring X Pinky
Index X Middle X Ring
Index X Middle X Pinky
Middle X Ring X Pinky

2 finger tests ( Includes 1 finger tests). Gives 12 Values
5- I can do thumb with any combination of the other finger
4 - I can do index finger with any combination of the other finger
2 - I can do middle finger with any finger except the pinky finger
1 -I can do ring finger with any finger except the pinky finger

12 + 8 + 4 = 28

28 Possible values with left hand assuming right hand is closed
28 Possible values with right hand assuming left hand is closed
28 Possible values with left hand assuming right hand is open
28 Possible values with right hand assuming left hand is open
28 values for each of the other 28 values is 28 * 28 = 784
28 + 28 + 28 + 28 + 784 = 896 possible signs I can make

*However this assumes I can make all 28 combinations with one hand with the other 28 possible values with the opposing hand. This will be the challenge of the user to train since our brains naturally oppose doing different things on the hands since our hands are controlled by one side of the brain ( I believe)

Add in the accelerometer, I can also introduce the concept of the speed one or both hands is moving in adding a third variable. This means the value from the state of the hands with their bent or not bent fingers being 00000  00000 ( all fingers are straight) could account for 4 values or more. Assuming I set the hands to either being slow or fast, then each finger combination with both hands could be slow - slow, slow - fast, fast - fast, fast - slow; with the slows or fasts coming from how fast each hand is moving. This will probably require testing to figure out and calibrate since slow and fast need to be calibrated to specific speeds.

This is the ideation. My next steps are to figure out the capabilities of the drive train and what I want to do with that. After that will be sending out my pitch on slack, once it gets approved/denied I can add features or start looking for the specific components I will use.

I need to figure out how to design the gloves, how to design the drive train, which components will work, and how much funding I will approximately need

I need the drive train to strafe in any direction ideally. Furthermore I want to make a cool looking design being cute and friendly. I need to make a pretty big display to show different stuff like time, battery, weather, date, and captions. I also need to make different faces that will belong to the robot. The robot should also have text to speech as well.

A simple drive train is easy to make. However weather might be difficult because it will require some type of connection. I can probably do date and time by setting the clock once then it keeps going forever and ever with only needing correction during daylight savings or other events like that. Battery should also be simple since it’s based on the battery capacity. 

**Total time spent: 1.5 hours**



# October 2

I'm thinking about making a Wall E referenced robot with deployable eyes that have built in cameras which broadcast to a screen like my phone or monitor what the cameras are seeing and I can control the robot by using my sensor gloves. The robot will preferably have a display in the front that displays additional info but im not sure what yet. 

The camera preferably needs a broad view so I can look around my surroundings and drive accurately. A small field of view will be difficult to drive. The ESP 32 S3 Sense has two camera sensors being the OV2640 or OV3660 sensors whom have an average horizontal FOV of 54°. My phone, the iphone 16e, has a horizontal FOV of 69°. 

I’m figuring out it’s quite difficult to figure out parts and make decisions on my own without the assistance of tutorials or peer advice. However, here is what I have determined.

My idea is a **Wall E inspired robot** that is controlled **remotely** with **hand gestures**. These gestures are expressed by using a glove that is fitted with sensors that detects whether or not **a finger is bent or straight**. Each finger will have its own sensor meaning that the bent state of one finger does not determine the nature of another finger. This allows for **numerous** combinations of my fingers allowing me to express lots of different commands to the robot simply by moving my hand around. This gives 2^10 possible combinations since each finger can be bent or straight and I have 10 fingers. However not every combination can be carried out since I don’t have **full flexibility and control over my digits**. An example of this is that it’s difficult for me to hold my pinky down whilst all the other fingers remain straight. This issue will require lots of testing for me to determine which hand signs are possible.
A **gyroscope** will be added to each glove to determine if my hand is parallel or perpendicular with the ground.
An **accelerometer** will be added to each glove to determine how fast my hand is moving. This can be made to give a hand sign two possible commands based on how fast it’s moving. For simplicity, I will most likely resort to two states of speed -– fast or slow — with some arbitrary values I determine myself.

Note, the robot will definitely not use all possible combinations that I can make simply because it cannot execute that many unique actions. The reason for the sensors is so I can differentiate the hand signs between each other. In reality, the robot is being controlled by orientation, speed, and finger state of my hand while to someone that doesn’t understand the code would assume that I programmed each hand sign to mean a specific thing. I essentially want to do **naruto** hand signs but this way I made it easier on myself to program and make unique hand gestures.

## Possible Additional Features
A display
- showing biometric data about the robot
- Time and Date
- Captions/text given by me from my keyboard or wireless connection

Speaker
- Output prerecorded audios that I can trigger with a hand sign
- I can type out messages and use a text to speech software to output the audio

Camera
- I want to be able to see what the robot sees and drive using the camera. It will send a live feed to some type of monitor, phone, or other display. The robot and display will connect over Wifi. Furthermore my plan is to put the cameras in the eyes of the Wall E design. However an issue with this is that 2 cameras showing the same perspective overlap and become useful. I can point one camera to the front and one camera to the back of the robot but then the vision will become lopsided.

LEDs
- An idea to fix the camera perspective issue is that I actually conceal the camera centered in the body of the robot. I will replace the cameras in the eyes with LED. This adds extra functionality and personality to the robot while still keeping full perspectives and not negatively affecting the vision. 
Rotatable hands and claws that can open or close but are non functional

An Image depicting my overall thought process of how everything will be connected and work
<img width="1504" height="980" alt="image" src="https://github.com/user-attachments/assets/465e459e-5c87-4527-bd5f-bdecc74a3e5d" />

**Total time spent: 3 hours**





