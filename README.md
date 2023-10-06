# pocketsphinx
The last (good) version written in C. Install sphinxbase first.

## Getting the application built on the machine

```
Clone and install pocketsphinx (NOT as sudo)
	Navigate to software storage directory
		cd ~/software
	Clone the pocketsphinx repo
		`git clone https://github.com/cartheur/pocketsphinx.git`
	Step into the new directory
		cd pocketsphinx
		./autogen.sh
		make
		sudo make install
	Refresh the configuration
		sudo ldconfig
	Check the installation
		pocketsphinx_continuous
```
If the autogen.sh file returns a permission denied error:

```
chmod +x autogen.sh
```

Copy the requisite model files for pocketsphinx, over ssh. On the host machine
	`cd /home/cartheur/software/`
   Find the IP address of the chip computer
	
```
curl ifconfig.me (public IP)
	ifconfig 	(private IP)
```

   Copy, will need root on the chip
	`scp -r pocketsphinx root@192.168.1.2:/usr/share`
   Test that the installation works
	
```
pocketsphinx_continuous \
    -hmm /usr/share/pocketsphinx/model/hmm/en_US/en-us \
    -dict /usr/share/pocketsphinx/model/lm/en_US/cmudict-en-us.dict \
    -lm /usr/share/pocketsphinx/model/lm/en_US/en-us.lm.bin \
    -inmic yes
```

   Hit ctrl-c to quit.
