# Vitis-IDE
This repo explains how to setup and install Vitis IDE for acceleration projects 
Vitis ide version is 2019.2 and works on Ubuntu 18.04

1- install Xilinix_Unified_2019 from the Xilinx website 
https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/vitis/archive-vitis.html 
![WhatsApp Image 2023-12-08 at 6 05 27 AM](https://github.com/Bassam-Kobasy/Vitis-IDE/assets/103467132/f07c75bf-95c4-4f51-88a6-40b366bcf1c7)

2-Install the following libraries:
sudo apt install libtinfo5
sudo apt install libncurses5

3- open the terminal in the directory of the installed file 
Extract the file and search for xsetup file
then run the installed file
sudo ./xsetup
Xilinx window should appear then click next and agree on all terms after that click next choose the first option "Vitis", then keep clicking next till it starts to install the program 

4- after the installation is finished, open the Xilinx website and download XRT through the following link
https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/embedded-platforms/archive-vitis-embedded.html 
and choose the suitable version for your Ubuntu 

![image](https://github.com/Bassam-Kobasy/Vitis-IDE/assets/103467132/19b949ba-28c8-4a95-8d17-ccf1d0577a26)

5- Download the required files of your board for example Zynq zc702
you need to download  the ZC702 Base 2019.2 file (for specific boards) and  Base Platform Cross-Compilation Sysroot for the Zynq family through the following link 
https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/embedded-platforms/archive-vitis-embedded.html
![image](https://github.com/Bassam-Kobasy/Vitis-IDE/assets/103467132/a5ee890a-66e1-46bc-b7fa-51f204bb9ca0)

6- In the terminal install the following libraries:
sudo apt-get install ocl-icd-libopencl1
sudo apt-get install opencl-headers
sudo apt-get install ocl-icd-opencl-dev

7- Install the XRT file that you have downloaded through the command 
sudo apt install ./xrt_2019...
after finishing the installation download the repo of xrt by typing in the terminal 
git clone --branch 2019.2 https://github.com/Xilinx/XRT.git 
then type 
Mkdir ~/Petabuilds
Cd ~/Petabuilds
8- Open the root directory and open opt/Xilinx, you should see a file named xrt 
open the terminal in the directory opt/Xilinx and type 
sudo mkdir platforms
then copy the  ZC702 Base 2019.2 file to platforms folder 
in the same terminal type 
cd platforms 
sudo unzip -q  ZC702 Base 2019.2

9- extract the Base Platform Cross-Compilation file and run sdk.sh file 
sudo ./sdk.sh

10- open the terminal and type 
cd /tools/Xilinx/Vivado/2019.2
source settings64.sh 
vivado
The Vivado window should appear 
open license manager choose load license and browse your license file which is named xilinxlc.li

11- Open the terminal and type 
source /tools/Xilinx/Vitis/2019.2/settings64.sh
source /opt/xilinx/xrt/setup.sh
then open the dirctory of the xrt repo that you have download any type 
cd <xrt_repo_directory>/XRT/src/runtime_src/tools/scripts 
you should find a file named xsa_build.sh
open the file and add the path link of the zc702_base_xsa.tcl(search about it in zc702_base folder)
then run the xsa_build.sh file by typing 
<xrt_repo_directory>/XRT/src/runtime_src/tools/scripts/xsa_build.sh 

12- Download  PetaLinux 2019.2 Installer from the Xilinx website through the following link
https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/embedded-design-tools/archive.html
![image](https://github.com/Bassam-Kobasy/Vitis-IDE/assets/103467132/7938b202-063c-4409-8611-289eec70ad52)
change the permission of the file by typing 
sudo chmod +x  PetaLinux 2019.2 Installer
then run it by typing 
./ PetaLinux 2019.2 Installer
then type 
Source /petalinux/2019.2/settings.sh
<xrt_repo_directory>/XRT/src/runtime_src/tools/scripts/peta_build.sh --bsp
./xsa_build/<platform name>/<platform name>.xsa

# Finally vitis ide is now installed 
you can open it by opening the terminal and type 
cd /tools/Xilinx/vitis/2019.2
source settings64.sh 
vitis


