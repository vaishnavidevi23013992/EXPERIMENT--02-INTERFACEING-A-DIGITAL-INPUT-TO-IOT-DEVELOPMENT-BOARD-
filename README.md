###  DATE: 24/09/2025

###  NAME: VAISHNAVIDEVI V
###  ROLL NO : 212223040230
###  DEPARTMENT: B.E-CSE


# EXPERIMENT--02-INTERFACING-A-DIGITAL-INPUT-TO-IOT-DEVELOPMENT-BOARD-
 

## Aim: To Interface a Digital Input  (IR pair ) to ARM IOT development board and write a  program to obtain  the data 
## Components required: STM32 CUBE IDE, ARM IOT development board,  STM programmer tool.
## Theory 
The full form of an ARM is an advanced reduced instruction set computer (RISC) machine, and it is a 32-bit processor architecture expanded by ARM holdings. The applications of an ARM processor include several microcontrollers as well as processors. The architecture of an ARM processor was licensed by many corporations for designing ARM processor-based SoC products and CPUs. This allows the corporations to manufacture their products using ARM architecture. Likewise, all main semiconductor companies will make ARM-based SOCs such as Samsung, Atmel, TI etc.

 
 # IR pair 
 
 ![image](https://user-images.githubusercontent.com/36288975/227598600-730748bf-9884-4a33-95bf-a1fbfde518ed.png)

 IR technology is used in a wide range of wireless applications which includes remote controls and sensing. The infrared part in the electromagnetic spectrum can be separated into three main regions: near IR, mid-IR & far IR. The wavelengths of these three regions vary based on the application. For the near IR region, the wavelength ranges from 700 nm- 1400 nm, the wavelength of the mid-IR region ranges from 1400 nm – 3000 nm & finally for the far IR region, the wavelength ranges from 3000 nm – 1 mm.The near IR region is used on fiber optic & IR sensors, the mid-IR region is used for heat sensing and the far IR region is used in thermal imaging. The range of frequency for IR is maximum as compared to microwave and minimum than visible light.  
## Procedure:
 1. click on STM 32 CUBE IDE, the following screen will appear 
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/4faea5c3-d246-4b0c-ab55-21f16d4d01f3" />

 2. click on FILE, click on new stm 32 project 
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/33b29dba-ca09-40b6-a249-052dedf501ae" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/592576ed-ebf3-43f4-85a6-38b0f6df2e7a" />
3. select the target to be programmed  as shown below and click on next 

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/3e428175-f331-4eaa-bca8-cf7a1e9255ff" />

4.select the program name 

<img width="487" height="538" alt="image" src="https://github.com/user-attachments/assets/0df0d203-9332-4bbd-abee-b7889532410f" />


5. corresponding ioc file will be generated automatically 
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/11ab3368-317c-4fd4-95db-1e1078d25fa5" />

6.select the appropriate pins as gipo, in or out, USART or required options and configure 
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ae2a22ff-14c6-41c7-9bfe-3e451f50ecdf" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9fba280f-4d34-4730-afc0-d8a30cfeaa6a" />


7.click on cntrl+S , automaticall C program will be generated 
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/694631f1-9174-4d74-bd77-c7eba356c4ab" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f1aa4d51-953a-48d3-806b-6bf01cbb29a2" />
8. edit the program and as per required 
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/742c7003-0c62-423a-860f-6ddf8986b6fc" />

9. use project and build all 
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/76208543-1d44-4771-89b6-764fb230c16b" />
10. once the project is bulild 
<img width="1088" height="480" alt="image" src="https://github.com/user-attachments/assets/ad427fba-7dfa-4b21-9a40-b1d057c54b70" />

11. click on debug option 
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/885331c0-d143-406d-b413-8a765bda94d0" />

12. connect the  iot board to power supply and usb 

13. After connecting open the STM cube programmer 
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ce2d4db7-eb67-4727-8d8a-409d162db674" />

14. click on UART and click on connect 
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/de8362f3-d699-424d-8581-0b3b09486eb4" />

15. once it is connected , click on Erasing and programming option 
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/bb6c61cd-fa07-4dac-b702-d39c10745254" />

16. flash the bin or hex file as shown below by switching the switch to flash mode 

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/78b4b6da-76bb-4cd9-9c3d-cfd3cea0b2d5" />


17. check for execution of the output by switching the board to run mode 



## STM 32 CUBE PROGRAM :
```
#include"main.h"
#include"stdbool.h"
void IRsensor();
bool IRsensorop;
```
```
while (1)
  {
	  IRsensor();
  void IRsensor()
  {
	  IRsensorop=HAL_GPIO_ReadPin(GPIOB,GPIO_PIN_3);
	  if(IRsensorop==1)
	  {
		  HAL_GPIO_WritePin(GPIOA,GPIO_PIN_0,GPIO_PIN_SET);
		  HAL_Delay(500);
		  HAL_GPIO_WritePin(GPIOA,GPIO_PIN_0,GPIO_PIN_RESET);
		  HAL_Delay(500);
	  }
	  else{
		  HAL_GPIO_WritePin(GPIOA,GPIO_PIN_0,GPIO_PIN_RESET);
		  HAL_Delay(500);
	  }
  }
```



## Output  :
### OFF state
<img width="1280" height="960" alt="image" src="https://github.com/user-attachments/assets/45c59b99-84f3-47b1-aa87-d7c9125a7e49" />

## ON state
<img width="1280" height="960" alt="image" src="https://github.com/user-attachments/assets/ce04a719-4fcf-44eb-b6f3-9573331ed240" />

 
 
 
## Result :
Interfacing a digital Input (ir pair) with ARM microcontroller based IOT development is executed and the results are verified.
