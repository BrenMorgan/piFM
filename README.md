# piFM
python pi FM
Steps to play sound:

(Created by Oliver Mattos and Oskar Weigl. Code is GPL)

sudo python
>>> import PiFm
>>> PiFm.play_sound("sound.wav")


Now connect a 70cm (optimally, ~20cm will do) or so plain wire to GPIO 4 (which is pin 7 on header P1) to act as an antenna, and tune an FM radio to 103.3Mhz.

Download the module here:

    [Download Now!]

(this contains both source and a ready to go binary. Just run the above code in the same folder. The antenna is optional, but range is reduced from ~100 meters to ~10cm without the antenna. The sound file must be 16 bit mono wav format. )
New! Now with stereo

sudo ./pifm left_right.wav 103.3 22050 stereo

# Example command lines
# play an MP3
ffmpeg -i input.mp3 -f s16le -ar 22.05k -ac 1 - | sudo ./pifm -

# Broadcast from a usb microphone (see arecord manual page for config)
arecord -d0 -c2 -f S16_LE -r 22050 -twav -D copy | sudo ./pifm -

How to change the broadcast frequency

Run the ./pifm binary with no command line arguments to find usage.

The second command line argument is the frequency to transmit on, as a number in Mhz. Eg. This will transmit on 100.0

sudo ./pifm sound.wav 100.0

It will work from about 1Mhz up to 250Mhz, although the useful FM band is 88 Mhz to 108 Mhz in most countries.

Most radio receivers want a signal to be an odd multiple of 0.1 MHz to work properly. 
