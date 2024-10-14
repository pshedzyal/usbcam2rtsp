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

- Web UI: `http://{IP}:1984`

Useful commands:
- To check the service status: `sudo systemctl status go2rtc.service`
- To view recent logs: `journalctl -u go2rtc.service --no-pager | tail -n 50`

## Configuration of go2rtc
### Raspberry Pi 4
This is draft version of the config for USB-connected camera that produces MJPEG or YUV422 streams. Trying to leverage hardware accelearation for H264 encoding using v4l2m2m.
```
streams:
  camera:   exec:ffmpeg -f v4l2 -input_format mjpeg -framerate 15 -video_size 1024x768 -i /dev/video0 -c:v h264_v4l2m2m -pix_fmt yuv420p -b:v 1M -fflags nobuffer -flags low_delay -tune zerolatency -f rtsp {output}
```
### Orange Pi Zero 3
In progress. Configuration for Orange Pi has to use different hardware acceleration solution. Probably a version with Rockchip MPP Support 
