# Vitis-IDE
This repo explains how to setup and install Vitis IDE for acceleration projects 
Vitis ide version is 2019.2 and works on ubuntu 18.04
1- install Xilinx_Unified_installer 2019.2 form the Xilinx website 
https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/vitis/archive-vitis.html 
![image](https://github.com/Bassam-Kobasy/Vitis-IDE/assets/103467132/717e44af-272c-4f2c-b8e0-2fbdfefdcbc3)
2- after installing it , change the permission of the file by right click on the file and go to permission tap and mark "Allow execution file as program" option  
3- open the terminal in the directory of the installed file 
Install the following libraries:
sudo apt install libtinfo5
sudo apt install libncurses5
then run the installed file
sudo ./Xilinx_Unified_2019.2.bin
Xilinx window should appear then click next and agree on all terms and after click next choose the first option "Vitis" , then keep click next till it starts to install the program 
4- after the installation is finished, open Xilinx website and download XRT through the folloinf link
https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/embedded-platforms/archive-vitis-embedded.html 
and choose the suitable version for your ubuntu 
![image](https://github.com/Bassam-Kobasy/Vitis-IDE/assets/103467132/19b949ba-28c8-4a95-8d17-ccf1d0577a26)
5- Download required files for you board for example Zynq zc702
you need to download  ZC702 Base 2019.2 file (for specific board) and  Base Platform Cross-Compilation Sysroot for Zynq family through the following link 
https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/embedded-platforms/archive-vitis-embedded.html
![image](https://github.com/Bassam-Kobasy/Vitis-IDE/assets/103467132/a5ee890a-66e1-46bc-b7fa-51f204bb9ca0)
5- In terminal install the following libraries:
sudo apt-get install ocl-icd-libopencl1
sudo apt-get install opencl-headers
sudo apt-get install ocl-icd-opencl-dev
6- Install the XRT file that you have downloaded through the command 
sudo apt install ./xrt_2019...
7- Open the root dirctory and oprn opt/xilinx , you should see a file named xrt 
open terminal in the dirctory opt/xilinx and type 
sudo mkdir platforms
then copy the  ZC702 Base 2019.2 file to platforms folder 
then in the same terminal type 
cd platforms 
sudo unzip -q  ZC702 Base 2019.2
8- extrat the Base Platform Cross-Compilation file and run sdk.sh file 
sudo ./sdk.sh
9- open the terminal and type 
cd /tools/Xilinx/Vivado/2019.2
source settings64.sh 
vivado
the vivado window should appear 
open license manager and choose load license and browes your license file which named xilinxlc.li
# finaly vitis ide is now installed 
you can open it by opening terminal and type 
cd /tools/Xilinx/vitis/2019.2
source settings64.sh 
vitis


