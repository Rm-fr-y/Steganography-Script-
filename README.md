# Steganography-Script
This short and simple script checks a file against multiple steganography tools.
The tools that are tested include steghide, stegseek, exiftool, zsteg, binwalk, foremost, outguess, strings, python3 (LSB extraction), and stepic. This script is designed to work on a debian or ubuntu based Linux machine. 

Please run the following commands before running this script to ensure that you meet the requirments to run this script. 
sudo apt update
sudo apt install -y steghide exiftool zsteg binwalk foremost outguess strings python3 python3-pip
sudo snap install stegseek
pip3 install Pillow
pip3 install stepic

Once you have the prerequiseties installed, to use the script do the following.
chmod +x stego_analyzer.sh #makes the script an executable
./stego_analyzer.sh target_file [wordlist]
The wordlist is for password bruteforcing. It is recommended to use rockyou.txt

The script creates an output directory named:
stego_results_<basename-of-target>
