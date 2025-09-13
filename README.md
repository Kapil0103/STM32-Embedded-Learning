# STM32 Embedded Learning Projects 🚀

This repository documents my **step-by-step journey of learning STM32 microcontroller programming**.
Each project demonstrates a fundamental concept in Embedded C, STM32CubeIDE, and debugging.  

---

## 📌 Projects Overview

1. [Project Creation & LED Pin Setup](#1-project-creation--led-pin-setup)  
2. [Compilation & Output Files](#2-compilation--output-files)  
3. [Programming using Bootloader](#3-programming-using-bootloader)  
4. [Programming & Debugging using ST-Link](#4-programming--debugging-using-st-link)  
5. [LED Blinker using Timer Interrupts](#5-led-blinker-using-timer-interrupts)  
6. [LED Blinker Debugging with Logic Analyzer](#6-led-blinker-debugging-with-logic-analyzer)  
7. [LED Blinker using Button Interrupts](#7-led-blinker-using-button-interrupts)  

---

## 1. Project Creation & LED Pin Setup

### 🎯 Objective  
Learn to create a new STM32CubeIDE project and configure a GPIO pin to blink an LED.  

### 🔹 Steps  
- Create new STM32 project in **STM32CubeIDE**.  
- Configure GPIO pin as **output** (e.g., `PA5` for Nucleo board LED).  
- Write code to toggle LED using `HAL_Delay()`.  
- Build & flash code.  

### 📖 Learning Outcome  
- Basics of STM32 project setup.  
- GPIO pin initialization.  
- First LED blink using software delay.  

---

## 2. Compilation & Output Files

### 🎯 Objective  
Understand the build process and different firmware file formats.  

### 🔹 Steps  
- Build project in CubeIDE.  
- Observe generated files in `/Debug`:  
  - `.elf` → Debuggable file.  
  - `.bin` → Binary for flashing.  
  - `.hex` → Intel HEX format.  

### 📖 Learning Outcome  
- Role of compiler, assembler, linker.  
- Difference between `.elf`, `.bin`, `.hex`.  

---

## 3. Programming using Bootloader

### 🎯 Objective  
Program STM32 using its built-in bootloader.  

### 🔹 Steps  
- Enter bootloader mode (BOOT0 pin high).  
- Connect via **STM32CubeProgrammer** (UART/USB).  
- Load `.bin` / `.hex` file → Flash.  
- Reset board to run code.  

### 📖 Learning Outcome  
- Bootloader vs. ST-Link.  
- Using STM32CubeProgrammer.  

---

## 4. Programming & Debugging using ST-Link

### 🎯 Objective  
Use ST-Link debugger for programming and real-time debugging.  

### 🔹 Steps  
- Connect **ST-Link V2** debugger to STM32 board.  
- Select **ST-Link** in CubeIDE.  
- Flash `.elf` file.  
- Use breakpoints and watch variables during debugging.  

### 📖 Learning Outcome  
- Programming STM32 with ST-Link.  
- Debugging with breakpoints, stepping, variable watch.  

---

## 5. LED Blinker using Timer Interrupts

### 🎯 Objective  
Blink LED using **hardware timer interrupts** instead of delay loops.  

### 🔹 Steps  
- Configure **TIM2** in CubeMX.  
- Set prescaler & ARR to 1 Hz.  
- Enable NVIC interrupt.  
- In ISR callback:
  ```c
  void HAL_TIM_PeriodElapsedCallback(TIM_HandleTypeDef *htim) {
      if (htim->Instance == TIM2) {
          HAL_GPIO_TogglePin(GPIOA, GPIO_PIN_5);
      }
  }
````

* Flash & observe LED blink.

### 📖 Learning Outcome

* Timer peripheral usage.
* Interrupt-driven code.
* CPU non-blocking approach.

---

## 6. LED Blinker Debugging with Logic Analyzer

### 🎯 Objective

Verify LED blink timing with a **USB logic analyzer**.

### 🔹 Steps

* Connect LED pin to logic analyzer input.
* Run timer interrupt blinker.
* Capture waveform in **Sigrok / Saleae software**.
* Confirm timing matches 1Hz blink.

### 📖 Learning Outcome

* Debugging with external tools.
* Verifying real signal timing.

---

## 7. LED Blinker using Button Interrupts

### 🎯 Objective

Toggle LED on **button press** using EXTI interrupts.

### 🔹 Steps

* Configure button pin as input with EXTI.
* Enable interrupt on falling edge.
* In ISR callback:

  ```c
  void HAL_GPIO_EXTI_Callback(uint16_t GPIO_Pin) {
      if (GPIO_Pin == GPIO_PIN_13) {
          HAL_GPIO_TogglePin(GPIOA, GPIO_PIN_5);
      }
  }
  ```
* Flash & press button to test.

### 📖 Learning Outcome

* External interrupt configuration.
* Handling real-world input events.
* Debouncing considerations.

---

## 🛠 Tools & Hardware Used

* STM32 Nucleo Board (STM32F4xx)
* STM32CubeIDE
* ST-Link V2 Debugger
* STM32CubeProgrammer
* USB Logic Analyzer (Saleae clone)

---

## 🎯 Final Takeaway

Through these projects, I practiced:

* STM32 project setup & GPIO programming.
* Compilation and firmware file formats.
* Bootloader programming & ST-Link debugging.
* Timer-based interrupts for precise control.
* External interrupts for button handling.
* Debugging with USB logic analyzer.

This structured journey helped me build strong foundations in **Embedded C programming** and **STM32 microcontroller development**.
