# Motion Bias Estimation (MBE)

---

Motion Bias Estimation is an experimental method of reducing drift.  
In simple terms, it uses the accelerometer to measure gyroscope bias, and then compensates for that without the need to put the tracker down.

# Shrimping

---

To take full advantage of Motion Bias Estimation, a process called "Shrimping" can be employed to assist with MBE calibration.
Motion bias estimation can only calibrate axes, that aren't aligned in the direction of gravity.

Shrimping is a method of being in a pose where none of the axes point directly up, so MBE can calibrate everything at once.  
Pose switching (going from laying down to sitting up) can assist with shrimping as it allows for the other axes to be calibrated.
Shrimping is not strictly required, but it can improve drift times.

##### Optimal Shrimping Pose:
![In-Game Exmaple of an optimal Shrimping Pose. Leaning back as if on a dentists chair at 45 Degrees. As a creative description, sitting like a Tetris S piece at 45 degrees onto your back.](https://imgur.com/AL2WL5q.png)

##### Image explaination:

![A Tinyslime example. It's standing straight up with it's IMU pointed towards the ceiling with a graphic drawn on it. Graphic shows XYZ planes and shows on the Z plane (Up) a "gravity" note. The graphic indicates that the Z axis cannot be recorded because it is in alignment with gravity.](https://imgur.com/AFINfb6.png)

![Another Tinyslime example. Depicting the tracker leaning back at a 45° angle with a graphic drawn on it. Graphic shows XYZ planes aligned with the tracker. The graphic indicates that the Z axis can now be recorded because it is not in alignment with gravity](https://imgur.com/OsreGVJ.png)
##### Image Sources: [Meia](https://discord.com/channels/817184208525983775/823930029070876736/1261446276889841704), [Meia](https://discord.com/channels/817184208525983775/823930029070876736/1261446549611745333)
