## pocketsphinx

The last (good) version written in C. Install [sphinxbase](https://github.com/cartheur/sphinxbase) first.

Get the 4.0.0 code [here](https://sourceforge.net/projects/cmusphinx/files/).

Read about the reasoned changes to `pocketsphinx_continuous` [here](https://cmusphinx.github.io/page3/).

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
   
Find the IP address of the remote computer, else, use the model files that come with the repository.

Next, run a speech recognition session with the microphone (live)
	
```
pocketsphinx_continuous \
    -hmm /home/ssoftware/pocketsphinx/model/hmm/en_us/en-us \
    -dict /home/software/pocketsphinx/model/lm/en_us/cmudict-en-us.dict \
    -lm /home/software/pocketsphinx/model/lm/en_us/en-us.lm.bin \
    -inmic yes
```

Hit ctrl-c to quit.
