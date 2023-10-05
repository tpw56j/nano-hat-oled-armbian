# NanoHAT OLED for Armbian - Python3 RC
NanoHAT OLED and GPIO Button Control for Armbian. This documentation contains installation and upgrade instructions.

## Disclaimer

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.

## Getting Started

### Prerequisites

Enable i2c0:
```
sudo apt update
sudo apt -y install armbian-config
sudo armbian config
```
Select `System`, `Hardware`, mark `i2c0` and `Save`. Reboot the system for the changes to take effect.

### Dependencies
Install the dependences from APT:
```
sudo apt -y install \
  libjpeg-dev \
  libfreetype6-dev \
  git \
  python3 \
  python3-dev \
  python3-pip \
  python3-setuptools \
  python3-smbus \
  python3-wheel \
  ttf-dejavu \
  zlib1g-dev \
  python3-libgpiod \
  python3-pillow
```

### Get the Code
Clone from GitHub:
```
cd /tmp
git clone https://github.com/crouchingtigerhiddenadam/nano-hat-oled-armbian
```

Run the code (optional):
```
cd /tmp/nano-hat-oled-armbian
python3 oled-start3.py
```
Use `ctrl+c` to terminate.

### Install
Make the program directory:
```
sudo install3.sh
```

Reboot the system for the changes to take effect.
```
sudo reboot now
```


## Troubleshooting

### Compatibility with BakeBit and NanoHatOLED
This does not require the FriendlyARM BakeBit or NanoHatOLED software to be installed. If this has already been installed you will need disable it.
```
sudo nano /etc/rc.local
```
Then find the lines:
```
/usr/local/bin/oled-start
exit 0
```
And comment out the `oled-start` line by adding `#` at the start of the line, so the lines look like this:
```
# /usr/local/bin/oled-start
exit 0
```
Save these changes by pressing `ctrl+x`, `ctrl+y` and `enter` as prompted at the bottom of the screen.   
   
Reboot the system for the changes to take effect.
```
sudo reboot now
```

### Problems on NanoPi Neo
I get
```
[Errno 16] Device or resource busy
```
and i have no idea how to fix

## Appendix

### Enable i2c0 through /boot/armbianEnv.txt
```
sudo nano /boot/armbianEnv.txt
```
Add `i2c0` to the `overlays=` line, for example if the line appears as follows:
```
overlays=usbhost1 usbhost2
```
Then add `i2c0` with a space seperating it from the other values:
```
overlays=i2c0 usbhost1 usbhost2
```
Save these changes by pressing `ctrl+x`, `ctrl+y` and `enter` as prompted at the bottom of the screen.  
    
Reboot the system for the changes to take effect:
```
sudo reboot now
```

