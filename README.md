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

after installation, the license manager will be opened 
add your license, then open terminal and type

cd /tools/Xilinx/xic/scripts

sudo ./installAIeDepLibs.sh

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

sudo apt install ./xrt_201920.2.3.1301_18.04-xrt.deb

after finishing the installation download the repo of xrt by typing in the terminal 

git clone --branch 2019.2 https://github.com/Xilinx/XRT.git 

then type 

sudo mkdir ~/Petabuilds

cd ~/Petabuilds

8- to check if the xrt is installed or not open the  directory /opt/Xilinx, you should see a file named xrt 
open the terminal in the directory opt/Xilinx and type

sudo mkdir platforms

then copy the  zc702_base_2019.2.zip file to platforms folder 

in the same terminal type 

cd platforms 

sudo unzip -q  zc702_base_2019.2.zip

9- extract the Base Platform Cross-Compilation file (sysroots_scripts.tar.gz) and run sdk.sh file 

sudo ./sdk.sh

10- Open the terminal and type 

source /tools/Xilinx/Vitis/2019.2/settings64.sh

source /opt/xilinx/xrt/setup.sh

then open the directory of the xrt repo that you have downloaded any type

cd <xrt_repo_directory>/XRT/src/runtime_src/tools/scripts 

you should find a file named xsa_build.sh
open the file and add the path link of the zc702_base_xsa.tcl(search about it in zc702_base folder)

![WhatsApp Image 2023-12-08 at 8 59 00 AM](https://github.com/Bassam-Kobasy/Vitis-IDE/assets/103467132/7e99a086-f03c-4ce5-b524-c0256feb10ce)

then run the xsa_build.sh file by typing 
<xrt_repo_directory>/XRT/src/runtime_src/tools/scripts/xsa_build.sh 

11- Download  PetaLinux 2019.2 Installer from the Xilinx website through the following link
https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/embedded-design-tools/archive.html
![image](https://github.com/Bassam-Kobasy/Vitis-IDE/assets/103467132/7938b202-063c-4409-8611-289eec70ad52)

to install petalinux you should follow this guid 
https://docs.xilinx.com/v/u/2019.2-English/ug1144-petalinux-tools-reference-guide 
*some tips for installing petalinux 
  1- you can install all required packages through this command 
 ` sudo apt-get install dos2unix iproute2 gawk make net-tools libncurses5-dev tftpd zlib1g:i386 libssl-dev flex bison libselinux1 gnupg wget diffstat chrpath socat xterm autoconf libtool tar unzip texinfo zlib1g-dev gcc-multilib build-essential screen pax gzip python 2.7.5`
 
  2- make sure to make the petalinux-v2019.2-final-installer.run file and the installation dirctory are not root using the following comand 
  
  sudo chown <user>:<user> petalinux-v2019.2-final-installer.run
  
  sudo chown <user>:<user> /opt/pkg/petalinux/2019.2
  
  on my Ubuntu it will be 
  
  sudo chown basssam:bassam petalinux-v2019.2-final-installer.run
  
  sudo chown bassam:bassam /opt/pkg/petalinux/2019.2

  3- if you faced any error in installation of petalinux make sure to delete petalinux_installation_log file before solving the error
  

12- then type 
source /opt/pkg/petalinux/2019.2/settings.sh
<xrt_repo_directory>/XRT/src/runtime_src/tools/scripts/peta_build.sh --bsp
./xsa_build/zc702_base/zc702_base.xsa

13- download y2k22_patch-1.2.zip 
follow the following link
https://support.xilinx.com/s/article/76960?language=en_US

# Finally vitis ide is now installed 
you can open it by opening the terminal and type 
cd /tools/Xilinx/vitis/2019.2
source settings64.sh 
vitis


