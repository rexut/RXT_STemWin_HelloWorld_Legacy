/**
  @page RXT_STemWin_HelloWorld Readme file

  @verbatim
  ******************************************************************************
  * @file    RXT_STemWin_HelloWorld/readme.txt
  * @author  MCD Application Team
  * @brief
  ******************************************************************************
  * @attention
  *
  * Copyright (c) 2018 STMicroelectronics.
  * All rights reserved.
  *
  * This software is licensed under terms that can be found in the LICENSE file
  * in the root directory of this software component.
  * If no LICENSE file comes with this software, it is provided AS-IS.
  *
  ******************************************************************************
  @endverbatim

@par Application Description

Simple "Hello World" example based on STemWin. Supported boards are:
  - 32F769IDISCOVERY, a.k.a. STM32F769I-DISCO, based on STM32F769NIHx
  - 32F723EDISCOVERY, a.k.a. STM32F723E-DISCO, based on STM32F723IEKx
  - STM32F7308-DISCO, a.k.a. STM32F7308-DK, based on STM32F730I8Kx

In this application, the code is executed from QSPI external memory while data
are in internal SRAM memory, except on systems with sufficient internal memory,
e.g. the STM32F723E_DISCOVERY based on STM32F723xx.

The application allows also to run the different Segger samples that can be
downloaded from here: http://www.segger.com/emwin-samples.html To do this,
user has only to replace the file "<TOP>/Src/BASIC_HelloWorld.c" into the
project workspace by the downloaded one.

Note that the following user files may need to be updated:
  <TOP>/Src/<BOARD>/LCDConf.c
  <TOP>/Src/<BOARD>/GUIConf.c
(if for example more GUI allocated memory is needed)

LED_RED and LED_GREEN are toggling continuously as a background task to
indicate that the application is running successfully.

@note Care must be taken when using HAL_Delay(), this function provides
      accurate delay (in milliseconds) based on variable incremented in
      SysTick ISR. This implies that if HAL_Delay() is called from a
      peripheral ISR process, then the SysTick interrupt must have higher
      priority (numerically lower) than the peripheral interrupt. Otherwise
      the caller ISR process will be blocked. To change the SysTick interrupt
      priority you have to use HAL_NVIC_SetPriority() function.

@note The application needs to ensure that the SysTick time base is always set
      to 1 millisecond to have correct HAL operation.

@par Keywords

Display, Graphic, STemWin, HelloWorld, LCD, GUI

@Note If the user code size exceeds the DTCM-RAM size or starts from internal
      cacheable memories (SRAM1 and SRAM2), that is shared between several
      processors, then it is highly recommended to enable the CPU cache and
      maintain its coherence at application level. The address and the size
      of cacheable buffers (shared between CPU and other masters) must be
      properly updated to be aligned to cache line size (32 bytes).

@Note It is recommended to enable the cache and maintain its coherence, but
      depending on the use case it is also possible to configure the MPU as
      "Write through", to guarantee the write access coherence. In that case,
      the MPU must be configured as Cacheable/Bufferable/Not Shareable. Even
      though the user must manage the cache coherence for read accesses.

      Please refer to the AN4838 "Managing memory protection unit (MPU) in STM32 MCUs".
      Please refer to the AN4839 "Level 1 cache on STM32F7 Series".

@par Directory contents

  - <TOP>/Inc/LCDConf.h                     Header for LCDConf*.c
  - <TOP>/Inc/<BOARD>/GUIConf.h             Header for GUIConf.c
  - <TOP>/Inc/<BOARD>/main.h                Main program header file
  - <TOP>/Inc/<BOARD>/stm32f7xx_hal_conf.h  Library Configuration file
  - <TOP>/Inc/<BOARD>/stm32f7xx_it.h        Interrupt handlers header file
  - <TOP>/Src/<BOARD>/LCDConf.c             Configuration file for the GUI library
  - <TOP>/Src/<BOARD>/GUIConf.c             Display controller initialization
  - <TOP>/Src/<BOARD>/main.c                Main program file
  - <TOP>/Src/<BOARD>/stm32f7xx_it.c        STM32F7xx Interrupt handlers
  - <TOP>/Src/<BOARD>/system_stm32f7xx.c    STM32F7xx system file
  - <TOP>/Src/BASIC_HelloWorld.c            Simple demo drawing "Hello world"

@par Hardware and Software environment

  - This application runs on STM32F730xx and STM32F723xx devices.

  - This application has been tested with STMicroelectronics STM32F7308_DISCO
    boards and can be easily tailored to any other supported device and
    development board.

  - This application has been tested with STMicroelectronics STM32F723E_DISCOVERY
    boards RevC and can be easily tailored to any other supported device and
    development board.

@par How to use it ?

In order to make the program work, you must do the following:

  1. Select required configuration in memory.h in Templates\ExtMem_Boot\Inc.
  2. Program the internal Flash with the ExtMem_Boot (see below).
  3. Program the external QSPI memory with this application (see below).
  4. Start debugging user application or reset for free running.

In order to load the ExtMem_Boot code :
  - Open your preferred toolchain :
    - Open the Project.
    - Rebuild all files.
    - Load project image.

In order to load this application to the external memory:
  - Open your preferred toolchain
    - Open the Project.
    - Rebuild all files.
    - Run & debug the program:
      - For an XiP configuration (eXecute in Place from QSPI):
        - Using EWARM or MDK-ARM: Load project image from the IDE: Project->Debug
        - Using STM32CubeIDE:
          - Open the STM32CubeProgrammer tool.
          - Select the QSPI external flash loader depending on board:
            - "MX25L512G_STM32F7308-DISCO.stldr" for STM32F7308_DISCO
            - "MX25L512G_STM32F723E-DISCO.stldr" for STM32F723E_DISCOVERY (not yet)
            - "MX25L512G_STM32F769I-DISCO.stldr" for STM32F769I_DISCOVERY (not yet)
          - From Erasing & Programming menu, browse and open the output binary
            file relative to your application.
          - Load the file into the external QSPI flash using "Start Programming"
            at the address QSPI_BASE (0x90000000).
      - For a standard configuration (sufficient internal memory):
        - Using EWARM or MDK-ARM: Load project image from the IDE: Project->Debug
        - Using STM32CubeIDE:
          - Open the STM32CubeProgrammer tool.
          - From Erasing & Programming menu, browse and open the output binary
            file relative to your application.
          - Load the file into the external QSPI flash using "Start Programming"
            at the address FLASH_BASE (0x8000000).


 */
