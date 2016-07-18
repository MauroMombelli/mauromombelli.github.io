Flight controller coparison

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
