# Steganography-Script
This short and simple script checks a file against multiple steganography tools.
The tools that are tested include steghide, stegseek, exiftool, zsteg, binwalk, foremost, outguess, strings, and stepic. This script is designed to work on a Debian or Ubuntu based Linux machine. 

<img width="2876" height="1466" alt="Script Running Image" src="https://github.com/user-attachments/assets/35bbed3e-3a5a-435d-989f-0a8bdfda9b57" />

Please run the following commands before running this script to ensure that you meet the requirements to run this script.
```
sudo apt update
sudo apt install -y build-essential autoconf automake libtool git wget binutils binwalk foremost libimage-exiftool-perl python3 python3-pip ruby-full steghide
sudo gem install zsteg
pip3 install Pillow
pip3 install stepic
#OR
pipx install stepic
wget https://github.com/RickdeJager/stegseek/releases/latest/download/stegseek_0.6-1.deb
sudo apt install ./stegseek_0.6-1.deb -y
rm ./stegseek_0.6-1.deb
git clone https://github.com/resurrecting-open-source-projects/outguess.git
cd outguess
./autogen.sh
sed -i '1 i\#define HAVE_PROTOTYPES 1' src/jpeg-6b-steg/jmorecfg.h
./configure --with-generic-jconfig
make
sudo make install
cd ..
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
Once the script is run you must specify if you want to run brute-forcing or not. Note: Brute-force on Outguess is time intensive, therefore use a short wordlist when using Outguess.

You may change the order in which the script is run. \
Syntax: toolname, toolname2, etc.

The script creates an output directory named: \
stego_results_(basename-of-target)
