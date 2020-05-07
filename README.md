# cube
Touch firmware for Cube i8 ultimate (ubuntu install).

0.0 sudo apt update && sudo apt upgrade
0.1 sudo apt install build-essential libelf-dev mc htop git curl openssh-server
0.1.1 mkdir ~/github
0.2 cd ~/github && git clone https://github.com/onitake/gsl-firmware && git clone https://github.com/onitake/gslx680-acpi
0.2.1 cd ~/github/gsl-firmware/tools && wget https://github.com/mateone4you/cube/raw/master/SileadTouch.sys && ./scanwindrv SileadTouch.sys
1.(fwtool)
cd ~/github/gsl-firmware/tools && ./fwtool -c firmware_00.fw -m 1680 -w 860 -h 1650 -f swap,track -t 5 silead_ts.fw
2.(copy)
sudo cp ~/github/gsl-firmware/tools/silead_ts.fw /usr/lib/firmware/
3.
cd ~/github/gslx680-acpi && rm ./gslx680_ts_acpi.ko
4.
make
5.
sudo insmod ./gslx680_ts_acpi.ko
5.1 sudo cp ./gslx680_ts_acpi.ko /lib/modules/5.4.0-29-generic/kernel/drivers/input/touchscreen/silead.ko
6.
sudo reboot
