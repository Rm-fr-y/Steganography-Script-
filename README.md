# Steganography-Script
This short and simple script checks a file against multiple steganography tools.
The tools that are tested include steghide, stegseek, exiftool, zsteg, binwalk, foremost, outguess, strings, python3 (LSB extraction), and stepic. This script is designed to work on a Debian or Ubuntu based Linux machine. 

Please run the following commands before running this script to ensure that you meet the requirements to run this script.
```
sudo apt update
sudo apt install -y steghide exiftool zsteg binwalk foremost outguess strings python3 python3-pip
sudo snap install stegseek
pip3 install Pillow
pip3 install stepic 
```
If you are running version 2.0 or lower, please run the following command first in order to allow the script to run properly. 
```
sed -i 's/\r$//' stego_analyze.sh
```
Once you have the prerequisites installed, to use the script do the following. \
chmod +x stego_analyzer.sh -- makes the script an executable \
./stego_analyzer.sh target_file [wordlist] \
The wordlist is for password brute forcing. It is recommended to use rockyou.txt
Once the script is run you must specify if you want to run brute-forcing or not. Note: Brute-forcing will not run Outguess. \
If brute-forcing is selected, you may change the order in which the script is run. \
Syntax: toolname, toolname2, etc.

The script creates an output directory named: \
stego_results_(basename-of-target)
