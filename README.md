# Steganography-Script
This short and simple script checks a file against multiple steganography tools.
The tools that are tested include steghide, stegseek, exiftool, zsteg, binwalk, foremost, outguess, strings, python3 (LSB extraction), and stepic. This script is designed to work on a Debian or Ubuntu based Linux machine. 
<img width="2876" height="1466" alt="Script Running Image" src="https://github.com/user-attachments/assets/35bbed3e-3a5a-435d-989f-0a8bdfda9b57" />
Please run the following commands before running this script to ensure that you meet the requirements to run this script.
```
sudo apt update
sudo apt install -y steghide libimage-exiftool-perl binwalk foremost binutils python3 python3-pip ruby-full build-essential
sudo gem install zsteg
wget https://github.com/RickdeJager/stegseek/releases/latest/download/stegseek_0.6-1.deb
sudo apt install ./stegseek_0.6-1.deb
sudo apt-get update && sudo apt-get install -y build-essential autoconf automake libtool git
git clone https://github.com/resurrecting-open-source-projects/outguess.git
cd outguess
./autogen.sh
./configure --with-generic-jconfig
make CFLAGS="-O2 -fcommon -std=gnu99 -Wno-error=implicit-function-declaration -Wno-error=incompatible-pointer-types -Wno-error=int-conversion -Wno-implicit-int -Wno-return-type"
sudo make install
pip3 install Pillow stepic
```
If you are running version 2.0 or lower, please run the following command first in order to allow the script to run properly. 
```
sed -i 's/\r$//' stego_analyze.sh
```
Once you have the prerequisites installed, to use the script do the following.
```
chmod +x stego_analyzer.sh # makes the script an executable
./stego_analyzer.sh target_file [wordlist]
```
The wordlist is for password brute forcing. It is recommended to use rockyou.txt
Once the script is run you must specify if you want to run brute-forcing or not. Note: Brute-forcing will not run Outguess. \
If brute-forcing is selected, you may change the order in which the script is run. \
Syntax: toolname, toolname2, etc.

The script creates an output directory named: \
stego_results_(basename-of-target)
