# Inertial Measurement Unit (IMU)

---

IMUs do the actual "tracking" of SlimeVR trackers. They measure the position and rotation of the tracker and feed that data to the controller which sends it to the SlimeVR server.

>Note: Purchasing IMUs from sources like AliExpress will not give you the full breakout board needed to join it to your board. Make sure the IMU you purchase is the full breakout board compatible with your PCB.

## Recommended IMUs & Drift Time:

### Performance:
- [BNO085](BNO085.md) - (30-60 Minutes)
- [LSM6DSO](LSM6DSO.md) - (40-50 Minutes)

### Value:
- [BMI270](BMI270.md) -  (20-30 Minutes)

### Budget:
- [BMI160](BMI160.md) - (10-20 Minutes)

#### Unsupported/Archive
- MPU
- Joycons

---

Certain IMUs are compatible with others and work the same. For example, BMI160 and BMI270's are typically exchangeable on the same board as they output the same type of data.