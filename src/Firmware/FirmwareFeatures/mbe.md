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

##### Image explaination:

![A Tinyslime example. It's standing straight up with it's IMU pointed towards the ceiling with a graphic drawn on it. Graphic shows XYZ planes and shows on the Z plane (Up) a "gravity" note. The graphic indicates that the Z axis cannot be recorded because it is in alignment with gravity.](https://cdn.discordapp.com/attachments/823930029070876736/1261446276646441063/image.png?ex=6693a5a4&is=66925424&hm=7baa7e022c292389d1651800581a403e3562c0dfd11b6a9214d8dc4ae8cc2bc8&)

![Another Tinyslime example. Depicting the tracker leaning back at a 45° angle with a graphic drawn on it. Graphic shows XYZ planes aligned with the tracker. The graphic indicates that the Z axis can now be recorded because it is not in alignment with gravity](https://media.discordapp.net/attachments/823930029070876736/1261446549326790786/image.png?ex=6693a5e5&is=66925465&hm=0d870e16a88bf6611f2053391a4917877ae4e4273421c26e6a178d7ca60cc203&=&format=webp&quality=lossless&width=976&height=1078)
##### Image Sources: [Meia](https://discord.com/channels/817184208525983775/823930029070876736/1261446276889841704), [Meia](https://discord.com/channels/817184208525983775/823930029070876736/1261446549611745333)
