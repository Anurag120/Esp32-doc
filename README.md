# Esp32-doc
A documentation to source the basic coding of Esp32


Set up the software environment for development of applications using hardware based on the Espressif ESP32.

Introduction

	ESP32 integrates Wi-Fi (2.4 GHz band) and Bluetooth 4.2 solutions on a single chip, along with dual high performance cores, Ultra Low Power co-processor and several peripherals. Powered by 40 nm technology, ESP32 provides a robust, highly integrated platform to meet the continuous demands for efficient power usage, compact design, security, high performance, and reliability.

	Espressif provides the basic hardware and software resources that help application developers to build their ideas around the ESP32 series hardware. The software development framework by Espressif is intended for rapidly developing Internet-of-Things (IoT) applications, with Wi-Fi, Bluetooth, power management and several other system features.


What you Need

	PC loaded with either Windows, Linux or Mac operating system
	Toolchain to build the Application for ESP32
	ESP-IDF that essentially contains API for ESP32 and scripts to operate the Toolchain
	A text editor to write programs (Projects) in C, e.g. Eclipse
	The ESP32 board itself and a USB cable to connect it to the PC


	Preparation of development environment consists of three steps:

	1. Setup of Toolchain
	2. Getting of ESP-IDF from GitHub
	3. Installation and configuration of Eclipse

	*You may skip the last step, if you prefer to use different editor.*

	Having environment set up, you are ready to start the most interesting part - the application development. This process may be summarized in four steps:

	1. Configuration of a Project and writing the code
	2. Compilation of the Project and linking it to build an Application
	3. Flashing (uploading) of the Application to ESP32
	4. Monitoring / debugging of the Application


Standard Setup of Toolchain for Windows

	Windows doesn’t have a built-in “make” environment, so as well as installing the toolchain you will need a GNU-compatible environment. We use the MSYS2 environment to provide this. You don’t need to use this environment all the time (you can use Eclipse or some other front-end), but it runs behind the scenes.

	Open a MSYS2 MINGW32 terminal window by running C:\msys32\mingw32.exe. The environment in this window is a bash shell. Create a directory named esp that is a default location to develop ESP32 applications. To do so, run the following shell command:

	mkdir -p ~/esp

	Getting Esp-IDF

		cd ~/esp

		git clone --recursive https://github.com/espressif/esp-idf.git

	Setup Path to ESP-IDF
		
		The toolchain programs access ESP-IDF using IDF_PATH environment variable. This variable should be set up on your PC, otherwise projects will not build. Setting may be done manually, each time PC is restarted. Another option is to set up it permanently by defining IDF_PATH in user profile. To do so, follow instructions specific to Windows , Linux and MacOS in section Add IDF_PATH to User Profile.

		The user profile scripts are contained in C:/msys32/etc/profile.d/ directory. They are executed every time you open an MSYS2 window.

		Create a new script file in C:/msys32/etc/profile.d/ directory. Name it export_idf_path.sh.

		Identify the path to ESP-IDF directory. It is specific to your system configuration and may look something like C:\msys32\home\user-name\esp\esp-idf

		Add the export command to the script file, e.g.:

		export IDF_PATH="C:/msys32/home/user-name/esp/esp-idf"
		Remember to replace back-slashes with forward-slashes in the original Windows path.

		Save the script file.

		Close MSYS2 window and open it again. Check if IDF_PATH is set, by typing:

		printenv IDF_PATH
		The path previously entered in the script file should be printed out.

	Start a Project
		Now you are ready to prepare your application for ESP32. To start off quickly, we will use get-started/hello_world project from examples directory in IDF.

		Copy get-started/hello_world to ~/esp directory:

		cd ~/esp
		cp -r $IDF_PATH/examples/get-started/hello_world .
		
		You can also find a range of example projects under the examples directory in ESP-IDF. These example project directories can be copied in the same way as presented above, to begin your own projects.