# TRS Tween

# What is TRS Tween?

TRS Tween smooths transitions by interpolating the **Translate**, **Rotate**, and **Scale** movements of players and Transform components. Setting position or rotation directly to target values creates abrupt, teleportation-like transitions.This is where Tween comes in, smoothly transitioning values between two states.

# How to Use

## Enabling Tween

Locate Tween in File > System Settings:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TRSinterpolation/image-20250901143110752.png" alt="image-20250901143110752" style="zoom:67%;" /> 

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TRSinterpolation/image-20250901143731900.png" alt="image-20250901143731900" style="zoom:67%;" /> 


Check this option to enable global TRS Tween.

![image-20250901143815783](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TRSinterpolation/image-20250901143815783.png) 

## Settings Explanation:

- Tween Methods

- Extrapolation: Object position is ahead of actual position, potentially causing brief clipping
- Interpolation: Object position is slightly delayed relative to actual position, partially reducing collision jitter

- Error Threshold: Timer starts when error exceeds this value; error is forcibly corrected after reaching the correction time limit

- Error Correction Timeout: When error exceeds the threshold, a timer starts. Once the correction timeout elapses, the error is forcibly corrected

- Maximum Error Limit: If error exceeds this value, it is immediately corrected

- Prediction Ratio: Adjusts the extrapolation Tween prediction scale. For example, 1.2 uses an additional 20% of values as the result. Reduce this value appropriately if object velocity frequently changes.

- Application Ratio: Adjusts the proportion of predicted values applied. For example, 0.8 uses 20% current data + 80% predicted data as the final result.
