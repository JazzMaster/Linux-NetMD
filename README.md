Linux netmd
========

several Linux NetMd utils are here from various authors and projects. ()nobody seems to have all of the pieces.)

putWave.py is a program for transferring songs to your NetMD device in SP mode via USB wire protocol (ATRAC3 codecs are not openly available-but used on PS3 also).

Dump_NetMD.py is an experimental - and tempermental- music dumper. 
(from linux-minidisc project)

It "commands" the device over USB  to playback the disc (and is supposed to record it if loopback alsa modules are loaded) back into WAV format. You can use mp3,ogg- whatever arecord will save to -or sox will convert to- later. I find personally- soundKonverter works in most cases(not all) - once you have the file.

The problem is getting an unknown TITLE from the disc (with spaces) to save in the first place.

PutWave script does the opposite- in data format. You can only FETCH audio in this manner IF its not marked as PROTECTED. The only workaround is audio playback (by hand).


(I may be able to pull -as WAV?- unprotected tracks.The problem is SonicStage protects tracks- but we can trip -on linux anyways-future writes to refuse the protection!! )

-It has some bugs. Some weird bugs. most python files here also need root level-or setUID USB access.

Its mostly safe to do so.


Example invocation
------------------

    $ ./netmd.py -f file.mp3

This command will transcode the song contained in file.mp3 to 16-bit PCM (big endian), extract its ID3 artist/title information, and transfer it to the first connected NetMD device it can find.
 
    $ ./netmd.py -h

Show help.

	$ sudo ./dump_md.py
	
This semi-automattic process takes over via USB control command sequences and proceedes(to try) to record audio on-the-fly with title information into a WAV(or other supported format).


There is a user interface for controlling the NetMD as a remote control(confirmed working with common NZ models) - available FOR LINUX and OSX. If we integrate these scripts with the HiNetMD Application(Qt/C) we might have a SonicStage alternative in conbination with system libraries and/or applications such as SoundKonverter (or sox). I know some Python TKinter programming(Its dodgy on OSX- QT may be a more viable option). 


What is left to do?
-------------------
Modifications to GetAudio scripts to do it like a file-in data mode, not just audio. It would be easier to check if track is protected first- 

	if so -
		then do audio- 
	if NOT- yank the data in as a WAV file.
	(most likely not stored in ATRAC format)

UI integration
Code optimizations and bug testing

The libnetmd library ideally needs to be modified to throw sane exceptions, as well as testing with Python 3. 

The libnetmd authors are working on the C version of the library.

Reverse engineering of ATRAC (for ATRAC 2 and 4 modes) as well as
code optimizations. The lack of these formats for either direction
waste space- moreso when putting data on a MD.

CDs-> MP3ish CDs




