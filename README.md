# STM32 VS Code Development Environment Set up

# Summary
This guide provides a basic setup for VSCode STM32 development environment.

# Requirements
- ARM-GCC toolchain
- CMake
- CMake Tools VS Code addon
- C/C++ for VS Code
- Cortex-Debug VS Code addon
- Ninja
- OpenOCD
- MSYS2
- STM32CubeMX
- STM32CubeCLT (for ST-link drivers) / Segger J-Link software pack (for J-Link drivers)

# Guide
- Install STM32CubeCLT from https://www.st.com/en/development-tools/stm32cubeclt.html#overview. This will install the ARM-GCC toolchain, CMake, and Ninja.
- Verify each was added to path by running "cmake --version", then "ninja --version", and finally "arm-none-eabi-gcc --version". All should return a version number.
- Install MSYS2 from https://www.msys2.org/. Open the MSYS2 window and run "pacman -S mingw-w64-x86_64-openocd". The toolchain will need to be added to the system path, it is typically found under "C:\msys64\mingw64\bin". Run "openocd --version" in a regular terminal to verify installation.
- Install STM32CubeMX from https://www.st.com/en/development-tools/stm32cubemx.html.
- Install Visual Studio Code if it is not already installed. Navigate to the extensions page and install the C/C++ extension, CMake Tools extension, and Cortex-Debugger extension.
- Clone this repo to your machine.
- Open CubeMX and initialize your project as normal. Navigate to the Project Manager tab and change the Toolchain/IDE to CMake. Once ready, press Generate Code.
- Open VS Code, press file->open folder and navigate to the folder that was created in the previous step.
- Delete the CMakeLists.txt in the root of this folder. Copy the .vscode folder and the CMakeLists.txt from this repo into the folder. Edit the sections in launch.json and CMakeLists.txt to match the hardware you are using.
- To build the project, press the build button in the bottom left of VS Code.
- To flash the code, either press ctrl+shift+p and type run task, click on Tasks: run task, then press Flash STM or navigate to the debug window on the left panel of VS Code, select STM32 Debug (openocd), and press the green play button. The second option will flash and launch the debugger.