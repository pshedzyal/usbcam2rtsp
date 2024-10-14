# usbcam2rtsp - RTSP video stream server from USB-connected camera

## Overview

This project provides instructions on how to set up RTSP server using SBC hardware (like Raspberry Pi or Orange Pi) and go2rtc software. The solution allows streaming video from USB-connected camera.

## Instructions

Depending on the installed OS, you may need to additionaly install 
Video4Linux package:
```bash
sudo apt-get install v4l-utils
```

and FFMPEG:
```bash
sudo apt-get install ffmpeg
```

Then, in order to install go2RTC, execute the following command in your terminal:
```bash
bash -c "$(wget -qO- https://raw.githubusercontent.com/pshedzyal/go2rtc-quick-setup/main/install.sh)"
```

## Usage

Once installed, you can use the following commands:

- To check the service status: `sudo systemctl status go2rtc.service`
- To view recent logs: `journalctl -u go2rtc.service --no-pager | tail -n 50`