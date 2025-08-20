# FRing

1. Flash Raspberry Pi OS Lite onto SD Card using Raspberry Pi Imager, and customize the setup to set username, password, hostname, and WiFi network.
2. Insert SD Card into Raspberry Pi Zero 2 W, and then connect to power source via micro usb.
3. Connect laptop to the same WiFi network the Raspberry Pi has been setup to use, and ssh into the Raspberry Pi.
4. Change username, password, network settings (nmcli) as needed.
5. sudo apt update and sudo apt upgrade
6. Connect USB hub to Raspberry Pi's micro usb port. Connect USB webcam to USB hub.
7. Check device is recognized using lsusb.
8. Find webcam by running 'v4l2-ctl --list-devices' (USB webcam is usually /dev/video0)
9. Try streaming
   Client: 'ffplay udp://@:12345'
   Host: 'ffmpeg -f v4l2 -framerate 15 -video_size 640x480 -i /dev/video0 -vcodec libx264 -preset ultrafast -tune zerolatency -f mpegts udp://<client-ip>:12345'
   Note: Client and RaspberryPi must have ffmpeg installed.
10. Setup NFS for easy file transfer and cross compilation for code editing
11. Check if python and pip are installed on RaspberryPi by using `python3 --version` and `pip3 --version`
12. If not installed, `sudo apt install python3` and `sudo apt install python3-pip`
13. Create virtual environment `python3 -m venv ~/fring`
14. Activate virtual environment `source ~/fring/bin/activate`. Use `deactivate` to exit virtual environment.
15. Install flask and opencv `pip install flask opencv-python`
