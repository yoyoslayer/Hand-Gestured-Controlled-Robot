---
title: "Lebronite"
author: "Yousif Hassanein"
description: "A short description of your project"
created_at: "2026-10-1"
---

# March 20: Wrote down the overall idea and first thoughts about the project

A drive train that is controlled with hand gestures.

The drive train will have the capabilities to strafe in any direction horizontally. The drivetrain will be programmed to follow a specific action based on the gesture created by the user's two hands. A hand gesture will be made by taking 2 types of data:
- Which fingers are bent and which fingers are not bent
- How fast each hand is moving. An accelerometer will be used to detect the velocity of the hand it is attached two.

The user will wear gloves that will have sensors detecting the nature of the user's fingers and how how fast the hands are moving. These gloves will then connect to the drive train using Wifi Capabilities given by an ESP 32. The drive train will also have an esp 32 module. 

The possible finger bent combinations that are possible are theorized to be 2^10 power. This is because I have 10 Fingers ( thank god) and depending on which fingers are bent and which fingers aren't bent there are this many possible combinations I can use. 

To visualize this, think of Binary and imagine all 10 fingers are assigned a value of either 0 or 1. If the finger is straight then its 0 and if the finger is bent then its 1.

Now imagine my hands are wide open and I'm showing my palms and all 10 fingers are straight. 

![Open Hands Image]("B:\New Downloads\Hands journal.jpg")

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
