The ability for an [[Operating System|operating system]] is dependent on a stack of software which allows for sound to be received from applications and output into devices. Audio software has various layers of abstraction above the initial audio hardware, these are:
- Audio hardware, such as sound cards, are used to input/output the sound either as analog or digital signals.
- Audio drivers, are used to interface with this audio hardware.
- Sound servers, are used to manage multiple audio inputs and outputs.
- Applications, which are processes which produce or receive audio.

# Audio Drivers
The lowest level of abstraction is the audio [[IO Devices#Drivers|driver]] level. These are used to directly interface with the hardware's sound card to display audio. User's are able to use these to determine audio-levels, equalisation and more. This can be done remotely given the user is a part of the `audio` group. There are two main audio drivers used throughout the Linux kernels life-span:
- **Open sound system** (OSS) were the original audio drivers found within the kernel. It was originally open source however after becoming proprietary software stopped being the main audio driver for the kernel.
- **Advanced Linux sound architecture** (**ALSA**) is the current kernel's audio driver system. It has greater support for USB, bluetooth, and MIDI devices as well as backwards compatibility with OSS.

# Sound Servers
Sound servers are the next layer of abstraction and allow for the multiplexing of audio inputs and outputs. This allows for multiple processes to write audio to the sound server, whereupon the sound is mixed by the sound server and then controlled through the audio drivers. Sound servers can also resample audio to provide better quality.

**Pulse audio** (PA) is a general purpose sound server that is known for its simplicity. It offers the same features as most sound servers and has the largest compatibility. Pulse audio can also be ran over the internet.

**JACK audio connection kit** (**JACK**) is a professional sound server that has greater flexibility than pulse audio. Its main features are lower latency, due to [[Distributed Computing#Time Synchronisation Algorithms|time synchronisation]] capabilities, and easier ability to control multiple sound cards. JACK has support for graphing applications that allow for the easy connection of various processes and audio devices, similar to a patch panel.

**Pipewire** is the new general purpose replacement for pulse audio, while also having the feature set of JACK. This has direct compatibility with both pulse audio and JACK at the cost of being a newer product, and thus having more bugs.