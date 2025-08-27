# Project Creation & LED Pin Setup

## 🎯 Objective
Learn how to create a new STM32CubeIDE project and configure a GPIO pin to blink an LED.

## 🔹 Steps
1. Open **STM32CubeIDE** → Create a new STM32 project.  
2. Select **Nucleo Board / STM32 MCU** (e.g., STM32F446RE).  
3. In **CubeMX configuration**:  
   - Enable a GPIO pin as **output**.  
   - Assign it to LED (usually `PA5` on Nucleo boards).  
4. Write code to toggle LED in `main.c`.  
5. Compile and run on the target board.  

## 🔹 Learning Outcome
- Basics of STM32 project setup.  
- GPIO pin initialization.  
- First LED blink using software delays (`HAL_Delay()`).  
