<h1 align="center">FAST TRACK 04</h1>
<h1 align="center">Makefile Assignment</h1>
<h5>Author: Pham Chinh Hiep</h5>
<h5>Account: HiepPC1</h5>
<h5>Date: 26 October 2023</h5>

![Dashboard](./Image/FPT_Software.jpg)

---
<!-- TABLE OF CONTENTS -->
<h2>Table of Contents</h2>
<ol>
  <li>
    <a href="#about-the-project">About The Project</a>
  </li>
  <li>
    <a href="#getting-started">Getting Started</a>
    <ul>
      <li><a href="#requirements">Requirements</a></li>
      <li><a href="#installation">Installation</a></li>
    </ul>
  </li>
  <li><a href="#how-to-use">How To Use</a></li>
  <li><a href="#additional">Additional</a></li>
  <li><a href="#contact">Contact</a></li>
</ol>

---
<!-- ABOUT THE PROJECT -->
## About The Project
This assignment need to write Makefile. Using **arm-none-eabi-gcc.exe** compile all source code and assembly code, generate object file and dependencies file. Then, **linker** all objects file to create file **S32K144_Demo.elf** load to **RAM** or **FLASH**.  

---
<!-- GETTING STARTED -->
## Getting Started
### Requirements
1. <a href="https://code.visualstudio.com/">Visual Studio Code</a>
2. <a href="https://ftp.gnu.org/gnu/make/">GNU Make</a>
3. <a href="https://developer.arm.com/downloads/-/gnu-rm">GCC for Arm</a>


### Installation
1. **Install and Setup GnuMake**
    - Download **GnuWin32** or **Cygwin** and setup environment variables for Windows
      - Add paths: Right Clicks **This PC** > **Properties** > **Advance system settings** > **Environment Variables** > **Path** > **Edit** > **New**

      - Examples: **C:\Program Files (x86)\GnuWin32\bin**

      - Open `cmd` type command to check:
        ```sh
        make --version
        ```
      - Install complete:
      ![INSTALL](./Image/make_complete.jpg)

2. **Install compiler for ARM**
    - If you have downloaded S32DS, you can also use the GCC version included in the S32DS with path: **…\S32DS.3.4\S32DS\build_tools\gcc_v9.2**
      ![INSTALL](./Image/gcc_arm.jpg)

---
<!-- HOW TO USE -->
## How To Use
1. **Open the terminal `Git Bash` and type:**
    ```sh
    cd Project_Demo/
    ```
2. **Export path for `GCC_PATH`:**
    ```sh
    export GCC_PATH=C:/NXP/S32DS.3.4/S32DS/build_tools/gcc_v9.2/gcc-9.2-arm32-eabi
    ```
3. **Type the following to clear output:**
    ```sh
    make clean
    ```
4. **Type the following to compile source code:**
    ```sh
    make compile
    ```
5. **Type the following to build and create file `S32K144_Demo.elf`:**
    ```sh
    make build LOAD_TO="option"
    ```
    - **option** is `FLASH` or `RAM`
    - Build complete on `FLASH`:
    ![BUILD](./Image/build_complete.jpg)
---
<!-- KNOWLEDGE -->
## Additional
1. **Calculate size of file (KB)**
    ```sh
    $(shell expr $(shell stat -c %s $(OUTPUT_DIR)/$(PROJECT_NAME).elf) / 1024 + 1)
    ```
    - `stat` to calculate size is bytes
    - `expr` to implement operations (`+`, `-`, `*`, `/`)  
2. **Print color in Makefile**
    - Table color:
      ```sh
      Black        |0;30     Dark Gray     |1;30
      Red          |0;31     Light Red     |1;31
      Green        |0;32     Light Green   |1;32
      Brown/Orange |0;33     Yellow        |1;33
      Blue         |0;34     Light Blue    |1;34
      Purple       |0;35     Light Purple  |1;35
      Cyan         |0;36     Light Cyan    |1;36
      Light Gray   |0;37     White         |1;37
      ```

    - Examples:
      ```sh
        BLUE = \033[0;34m
        RED = \033[1;31m
        YELLOW = \033[1;33m
        WHITE = \033[1;37m
        GREEN = \033[0;32m
        RESET = \033[0m
      ``` 
    - Command:
      ```sh
      @echo -e "\n$(RED)Size: $(shell expr $(shell stat -c %s $(OUTPUT_DIR)/$(PROJECT_NAME).elf) / 1024 + 1) KB $(RESET)"
      ```
---
<!-- CONTACT -->
## Contact

* Email   :  [hieppc1@fpt.com](hieppc1@fpt.com)
* Phone   :  0973109103
* Github  :  [https://github.com/github_username/repo_name](https://github.com/github_username/repo_name)

