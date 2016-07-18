---
layout: default
title: Flight controller hardware comparison
excerpt: this is a little comparison of Flight Controller for multicopter as of 2016-07
---

# {{page.title}}

{{excerpt}} 

This comparison whant to clear up the main differencies on the flight controller. Those are POTENIAL capability of the flight controller, but there are some thing to keep in mind:
- MCU/FPU speed is desired to get more CPU time to let the software do other stuff. if you just want to fly even an atmega with some good quality code is fine
- double support is needed only if you want GPS navigation
- how the hardware is connected. A clear example of this is shared HW on multiple pin, or the lack of connection to all MPU pin. This is not taken into consideration
- Sensor's update time VS ouptut bit
- Software capability (aka: you may have the best HW but if the sowtare doesn't manage to use it..)
- FC are relatively cheap and extremly hard to break even on hard crash

So my opinion is to buy the best HW with active development and lot of user. Bonus point if it is supported by multiple project and its openharware, as this helps a lot the development of alternative software and hardware.

| FC | MCU | IMU | BUS* |
|----|-----|-----|-----|
| AfroFlight Naze32 Rev5 | no FPU (stm32f1) | only 6DOF (MPU6050) | i2c |
| Naze32 Rev5 Full | no FPU (stm32f1) | 9DOF + baro (MPU6050) | i2c |
| Naze32 Rev5 Full | no FPU (stm32f1) | 9DOF + baro (MPU6500) | i2c |
| CC3D | no FPU (stm32f1) | 6DOF (MPU6000) | ? |
| OpenPilot Revo | very good mpu (STM32F405RGT6) | 9dof + baro (MPU-6000 + HMC5883L + MS5611) | SPI |
| Naze flip 32 | no FPU (stm32f1) | 9DOF + baro (MPU6050 + HMC5883L + MS5611) | i2c |
| Mini APM V3.1 | no FPU, low clock, flash, ram, no double (atmega2560) | 9DOF (?) + GNSS (GPS only, no Glonass, Galileo or  differential correction) | i2c |
| Hobbyking KK2.1.5 | no FPU, low clock, flash, ram, no double (atmega266) | 6DOF (6050MPU) | i2c |
| Seriusly Pro f3 | good MPU + FPU (stm32f3) | 6DOF (MPU6050) or 9DOF +baro (HMC5883 + MS5611) | i2c |
| Seriusly Pro f3 EVO | good MPU + FPU (stm32f3) | 9DOF +baro (MPU9250 + BMP280) | SPI |
| MOTOLAB TORNADOFC | ? | ? | ? |
| Seriusly dodo | good MPU + FPU (stm32f3) | 6DOF (MPU6050) | i2c |

(* main bus used to talk with Gyroscope and Accelerometer)
