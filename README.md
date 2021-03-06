# Universal_HamRadio_Remote_HTML5
Universal HamRadio Remote HTML5 interface.<br>
This is an implementation of a python server and HTML5 frontend to provide a web interface to use your TRX for both RX and TX.<br>
You can use basic and some advanced functions of your radio.<br>
You use the speaker and microphone of your computer to communicate.<br>
This project is more oriented for voice (phone) or CW.<br>
<br>
Caution:<br>
It is designed for Raspberry Pi OS (32-bit) Lite (actually "Minimal image based on Debian Buster").<br>
Use only if it is legal in your country.<br>
It is intended for remote use, it is not designed for use on the same computer as an interface even though it will likely work.<br>
Please don't raise an issue for anything outside of the intended design.<br>
<br>
![alt text](README/UHRR_Pict.png)

This utility is used to set up an amateur radio station remotely via a web browser.

You need:
- a radio station compatible with Hamlib.
- a cat interface.
- a circuit making it possible to adapt the audio levels between the microphone input, the speaker output and the sound card.

Assuming your raspberry pi hostname is set to UHRR, you can access it at https://UHRR.local:8888/
Note the HTTP <b> S </b>.
You can configure all of this by logging into https://UHRR.local:8888/CONFIG
If the original configuration is invalid or missing, this will automatically switch to the configuration page.


![alt text](README/func_princ.png)

![alt text](README/sound_diagram.png)

## Requirements:
```
sudo apt-get install -y git python3 python3-pip python3-libhamlib2 python3-numpy python3-tornado python3-serial python3-pyaudio
sudo pip3 install pyalsaaudio
```

## Installation:
```
cd ~/
git clone https://github.com/F4HTB/Universal_HamRadio_Remote_HTML5.git
cd Universal_HamRadio_Remote_HTML5
sudo cp selfsign.crt /boot/UHRH.crt
sudo cp selfsign.key /boot/UHRH.key
./UHRR
```
## Optional:

```
sudo apt-get install screen

add in /etc/rc.local the command to run at startup:

sudo nano /etc/rc.local
copy and past: runuser -l pi -c '(cd /home/pi/Universal_HamRadio_Remote_HTML5/ && ./UHRR >> /tmp/uhrr.log) &'
```
![alt text](README/UHRR_conf_Pict.png)

```
[SERVER]
SERVER port: the server port

[AUDIO]
AUDIO outputdevice: output from audio soundcard to the mic input of TRX
AUDIO inputdevice: input from audio soundcard from the speaker output of TRX

[HAMLIB]
HAMLIB com port: com port of the CAT interface
HAMLIB radio model: hamlib trx model
HAMLIB auto tx poweroff: set to auto power off the trx when it's not in use
```
## Possible problem
No //is for get some problemes from the code
## Other optional
To get more functionality you can use the latest version of HamLib
```
git clone https://github.com/Hamlib/Hamlib
cd Hamlib
./bootstrap
./configure --with-python-binding PYTHON=$(which python3)
make
sudo make install
cd bindings
make
sudo make install

```
And finally now run with:
```
PYTHONPATH=/usr/local/lib/python3.7/site-packages:$PYTHONPATH ./UHRR
```

Special thanks to :

-Mike W9MDB! and all the hamlib team for all their hard work

-All contributors :)
