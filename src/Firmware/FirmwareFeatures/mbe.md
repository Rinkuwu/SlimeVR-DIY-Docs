# Motion Bias Estimation (MBE)

Motion Bias Estimation is an experimental method of reducing drift.  
In simple terms, it uses the accel to measure gyro drift, and then compensates for that without the need to put the tracker down.

---
# Shrimping

To take full advantage of Motion Bias Estimation, its possible to "Shrimp".  
Motion bias estimation can only calibrate axes, that arent directly in the direction of gravity.  
Shrimping is a method of being in a pose where none of the axes point directly up, so MBE can calibrate everything at once.  
Its also possible to switch poses in order to change which axes is not calibrated. For example, you could stand for a bit, and then lie down for a bit, or switch between lying on your back and your side.  
This is not strictly required, but it can improve drift times.
