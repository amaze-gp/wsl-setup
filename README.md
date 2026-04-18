# wsl-setup

## Method 1: Using Windows Terminal (Recommended)
Open PowerShell as Administrator: Right-click the Start button, select "Terminal (Admin)" or "PowerShell (Admin)".
Run Install Command: Type wsl --install and press Enter.
This command enables required features, downloads the latest Ubuntu LTS, and installs it.
Restart Computer: Restart your PC when prompted to finalize installation.
Set Up Ubuntu: After rebooting, a terminal window will open automatically to complete installation. Create a username and password for your Ubuntu environment.

if the error is showing up like below then please follow the steps 

Error 
-----
WSL2 is not supported with your current machine configuration.
Please enable the "Virtual Machine Platform" optional component and ensure virtualization is enabled in the BIOS.
Enable "Virtual Machine Platform" by running: wsl.exe --install --no-distribution
For information please visit https://aka.ms/enablevirtualization
Error code: Wsl/InstallDistro/Service/RegisterDistro/CreateVm/HCS/HCS_E_HYPERV_NOT_INSTALLED 
-----


To resolve this error, you need to complete two steps: enabling the feature in your Windows settings and enabling the technology in your hardware (BIOS/UEFI). 
Follow these steps in order:

## Step 1: Enable Windows Features
Open the Start Menu, type Turn Windows features on or off, and press Enter.
In the list that appears, find and check the following two boxes:
Virtual Machine Platform
Windows Subsystem for Linux
Click OK.
Do not restart yet (unless you are sure Virtualization is already on in your BIOS). 

## Step 2: Enable Virtualization in BIOS (The "Hardware" Step) 
Even if you turn on the software in Windows, it won't work if your CPU's virtualization is disabled at the motherboard level. 
Check if it's already on:
Right-click the Taskbar and open Task Manager.
Go to the Performance tab and click CPU.
Look for Virtualization: in the bottom right. If it says Disabled, you must proceed with the steps below.
Enter BIOS: Restart your computer. As it is booting up, repeatedly tap the BIOS key (usually F2, F10, F12, or Del depending on your PC manufacturer).
Find the setting: Look for a menu named "Advanced," "CPU Configuration," or "Security."
Enable the toggle:
For Intel CPUs: Look for VT-x, Intel Virtualization Technology, or Vanderpool. Set it to Enabled.
For AMD CPUs: Look for SVM Mode or Secure Virtual Machine. Set it to Enabled.
Save and Exit: Press F10 to save changes and restart into Windows. 

## Step 3: Set WSL to Version 2 
Once you are back in Windows, you need to ensure WSL is actually trying to use version 2. 
Open PowerShell or Command Prompt as Administrator.
Run the following command:
powershell
wsl --set-default-version 2
If you get a message saying "WSL 2 requires an update to its kernel component," download and install the package from aka.ms/wsl2kernel. 

## Method 2: Using the Microsoft Store
Open the Microsoft Store and search for "Ubuntu".
Select the latest Ubuntu LTS version (e.g., Ubuntu 24.04).
Click "Get" or "Install".
Once downloaded, click "Open" and set up your username and password.
