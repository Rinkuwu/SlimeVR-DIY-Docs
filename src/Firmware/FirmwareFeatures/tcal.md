# Temperature Calibration (TCAL)

---

Tempature calibration is the process of lowering and raising the tempeature of the tracker so that it can record it's acceleration data at different temperature points and can apply that as an offset to combat drifting.

TCAL is available for BMI160 IMUs on any recent firmware. BMI270 TCAL is available only on l0ud/main firmware. LSM6DSO and BNO085 do not have any TCAL implimentation (and they don't really need it).

TCALv2 is better and supercedes TCALv1, though v1 is still present and data is collected for both during the process. [Source](https://discord.com/channels/817184208525983775/823930029070876736/1130053326264873010)

If possible, TCAL is easist to perform on a heated 3d printer bed. The slightest amount of movement will abort the tcal calibration. So make sure it's performed on a stable non-moving surface. 

## TCALv1:
<details>
<summary>Instructions</summary>

[Source](https://discord.com/channels/817184208525983775/999926371218374666/1088821937918201906): [Astrocast](https://discordapp.com/users/201141322373922817)

> For those that want to attempt v3dev BMI160 TCAL, a very rough guide on how to do so:
>
>It is recommended to detach the battery from your tracker during this whole process as it will not be used during this process and runs the risk of being damaged if heated too much.
>You will need:
>-Your tracker
>-A refridgerator or freezer
>-A micro usb cable to connect your tracker to pc. You should already have this.
>-A heater of some kind. I used a small room heater that blows warm air.
>
>Software wise, you'll need:
>-Slimevr server
>-A serial terminal. You can use Visual Studio Code, Arduino IDE, or any other serial terminal of your choosing. slimevr's serial terminal will not work because it doesnt allow you to send commands to the tracker which is necessary for this process. I recommend using the Arduino IDE because its fairly easy.
>
>TCAL is a process that involves collecting calibration data at several different temperatures within the range of 15C to 45C. On the latest v3dev firmware, if a tracker is held still at a temperature point that doesnt contain data, it will record TCAL data for that temperature point. There are 60 different temperature points between the temperature range of 15C to 45C, each roughly 0.5C apart from one another.
>When a slimetracker is powered on, it begins recording TCAL data automatically whenever the tracker is held still at a temperature point that doesnt contain TCAL data. This data is stored in RAM, and will not be saved to storage or used unless a command is sent to the tracker. So, the goal here is to slowly have our tracker reach every temperature point while being held still, from 15C to 45C, and to save our progress by sending commands to the tracker. 
>
>You can do this by following these steps:
>
>1. Cool your tracker to a little below 15C. You can do this by placing your tracker in a refridgerator to cool it down. Remember, it's recommended to remove the battery before doing any of this as we will not be using it. It shouldn't take too long for your tracker to get cold enough. Once you think its cold enough, take it out and move on to the next step.
>
>2. Connect your tracker to your PC via USB, placing the tracker on a flat level surface where it won't be moved.
>
>3. Open your preferred serial terminal and connect to the tracker's COM port. (This should be done BEFORE you open Slimevr server, otherwise slimevr server will grab the COM port automatically and prevent your terminal from accessing it. For reference, the tracker will likely be using a baud rate of 115200. If the text in the terminal still looks like gibberish or question marks, try other baud rates.)
>
>4. Open slimevr server. Allow the tracker a moment to connect, which will allow you to see the tracker's current temperature.
>
>5. Check to be sure that the tracker's current temp is at or below 15C. If it is, then move on to the next step. If it isn't, go back to step 1 and repeat steps 1-5.
>
>6. Keep it still and allow your tracker to slowly reach room temperature. As the temperature rises, occasionally check the tracker's TCAL data by sending the command "TCAL DEBUG" in the serial terminal. This command allows you to see all 60 TCAL data points, with the first number in each point being the temperature the point was recorded at. Once your tracker starts rising above 15C, you should see these points start to be filled. Once your tracker reaches room temperature (meaning the tracker stops rising in temperature) you're ready to move on to the next step.
>
>7. Check your TCAL data once more with the "TCAL DEBUG" command. If your tracker's temperature rose too fast, or your tracker was moved during step 6, your tracker might have missed a temperature point. If a temperature point was missed, you'll have to save your current TCAL data and go back to step 1, repeating steps 1-7. To save your current TCAL data, send the command "TCAL SAVE" to the tracker. Once you do that, it is safe to unplug the tracker from your PC. If there are no missed temperature points thus far, then "TCAL SAVE" your current TCAL data, unplug your tracker and move on to the the next step.
>
>8. Heat your tracker to 45C. There are many ways to do this, but what I did was I placed my tracker in front of a small room air heater with the heater set to its lowest setting. To check whether it was hot enough, I plugged my tracker back into USB while it was heating and opened up slimevr server to check it's temperature reading. I then waited until the tracker reached 45C. Once it did, I unplugged it and closed slimevr server. After heating your tracker, repeat steps 2-4 to hook your tracker back up again and place it on a flat surface. Then move on to step 9.
>
>9. Check to be sure that the tracker's current temp is at or slightly above 45C. If it is, then move on to the next step. If it isn't, go back to step 8.
>
>10. Once again, keep your tracker still and allow your tracker to slowly reach room temperature. As the temperature lowers, check the tracker's TCAL data by sending the command "TCAL DEBUG" in the serial terminal. Allow your tracker to cool until all the points in TCAL DEBUG are filled, then move on to the final step. (If your tracker stops cooling and isn't getting cool enough to reach all the temperature  points that are left, you can place a fan next to the tracker to cool the air around it, or place a glass of ice near the tracker to cool the surface it is sitting on.)
>
>11. Just as we did in step 7, Check your TCAL data one final time with the "TCAL DEBUG" command. If a temperature point was missed, you'll have to save your current TCAL data with "TCAL SAVE" and go back to step 8 to heat your tracker again. You can also type "TCAL PRINT" and check if the calibration percentage has reached 100. 
>
>If all the points shown in "TCAL DEBUG" are filled, then congrats, you completed TCAL! TCAL data should save automatically when all the points are filled in, but just in case, you can save your TCAL data with the TCAL SAVE command one more time. Then you're done!
</details>

## TCALv2:

<details>
<summary>Instructions</summary>

[Source](https://discord.com/channels/817184208525983775/999926371218374666/1092298346665873449): [Astrocast](https://discordapp.com/users/201141322373922817)

> yes, cool your tracker to below 15C, then place it on a flat stable table where it wont be moved. Then power it and monitor its temps. You need to then slowly heat the tracker to 45C while letting it sit still, but don't heat it too quickly (you can let heat up on its own for a while before applying heat with something). If you manually flash the tracker using Visual Studio you can flash it with a setting that sends tcal debug info to the slimevr server, telling you when it is in calibration mode and when it finishes. This is not necessary, but it can let you know for certain that it has started/stopped calibrating. Calibration starts automatically when it is cooled to 15C and stops and saves once 45C is reached. If cooled to below 15C, it wont start collecting data until it reaches 15C, so that can give you time to position it where you want. Be sure to flash your trackers with the latest firmware if you havent in a while, because there was a bug a little while ago where tcal data wouldnt save when 45C was reached. 

</details>
