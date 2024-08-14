[Important]
Make sure to set your orangepi's IP address to 'Static'/'Manual' in the network admin page of your router.
You can typically get to the admin page by typing '192.168.0.1' in your browser
If that doesn't work lookup your router on google and follow those steps.
Default login for network admin page is 'username:admin' 'password:admin/password/password1'
Default login for orangepi 'username:root' 'password:orangepi'

[update ubuntu]
sudo apt-get update
sudo apt-get upgrade

[install dependencies]
sudo apt-get install usbmuxd libimobiledevice6 libimobiledevice-utils
sudo apt-get install wget curl libavahi-compat-libdnssd-dev
sudo apt install python3-pyqt5 python3-pip
python3 -m pip install --upgrade pip
pip3 install pyinstaller
sudo apt-get install avahi-daemon
systemctl start avahi-daemon.service
systemctl start avahi-daemon.socket
systemctl enable avahi-daemon.service
systemctl enable avahi-daemon.socket
pip install requests

[install altserver]
curl https://raw.githubusercontent.com/powenn/AltServer-Linux-PyScript/rewrite/main.py > main.py
python3 main.py

[run altserver on boot]
Without this, you'll have to type in 'python3 main.py' every time your reboot your orangepi

sudo crontab -e
option 1
@reboot python3 main.py &
