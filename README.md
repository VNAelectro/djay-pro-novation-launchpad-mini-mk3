# Launchpad Mini MK3 MIDI Mapping for Algoriddim djay Pro (with dynamic RGB color for CUE pads)

Hey everyone! As a fellow casual DJ and electronic music producer, I'm excited to share a project born from my passion for music and for customizing my setup to match my creative needs.

I’ve been a happy user of [Algoriddim's djay Pro](https://www.algoriddim.com/djay-pro-mac) for a few years now, and I absolutely love its power and flexibility, especially the ability to use it on both my MacBook and iPhone. My modular approach to DJing has served me well, and my trusty Reloop Mixtour was a fantastic companion. However, when I looked at the new Mixtour Pro, I thought I would love to have it but quickly realized I couldn't stand the extensive use of multiple assignments for pads and buttons. I'm a big believer in a **one pad, one function** philosophy for a clear and intuitive workflow. And to be honest, my Mixtour works really well and I don’t see any good reason to replace it ^^

My search for a **modular MIDI controller** with plenty of pads led me to the **Novation Launchpad Mini MK3**. I discovered its "Programmer Mode," which allows the host application to **take full control of the RGB pads**. Bingo! This was the perfect solution I had been looking for.

### The Project

Mapping the standard MIDI functions in djay Pro was a breeze thanks to its MIDI controller configuration feature. However, the interface only allows you to set a minimum and maximum value to display colors for the two states of a button. This works well for most functions, but since **djay Pro lets you customize the cue point colors, I wanted those colors to be visible on my Launchpad!** 
The trickiest part was aligning the Cue Pad colors with the ones defined in the app. To achieve this, I had to edit the config file directly (in XML format). This feature isn’t well documented, but after some reverse-engineering of other XML config files, I finally cracked it.

Djay Pro lets you also assign a **MIDI shift button** for controllers that don’t have a built-in shift key. In my final mapping, I used this soft MIDI shift feature provided by the software, which is very useful, especially because the Launchpad Mini MK3 doesn’t have a hardware shift button in Programmer Mode. Thanks to this, the Launchpad Mini MK3 effectively gives you access to 160 pads: 80 normal pads plus 80 more when using the shift button, greatly expanding your control options.
Note that since the shift function is managed in the software, there’s no way to change the pads’ RGB colors when pressing shift to reflect their alternative functions. It’s not a big deal, though, as I made sure to keep the main and shift functions coherent.

Now we have it: **the ultimate low-cost control pad for djay Pro and the ideal companion to my good old Mixtour!** 
I now use the Mixtour strictly as a mix table for EQs, Neural Mix, track volume, and library navigation, completely removing the need for its shift key functions.

### My Mobile Setup

My modular setup is quite simple and incredibly portable.
* An iPhone connected to a **USB-C hub** that includes a Power Delivery (PD) input port.
* The Reloop Mixtour and Launchpad Mini MK3 are both connected to the hub.
* An external USB-C power source keeps everything running. This setup even works with a simple power bank for ultimate mobility!

### Walkthrough 

**Installing the Config File in djay Pro**

1. Download the attached configuration file named: *Launchpad MK3 DynRGB.djayMidiMapping*
2. Open your file explorer and double-click the file to open it with djay Pro.
3. When prompted, click OK to confirm the installation of the config file.
4. The config file is now installed, but you need to connect the Launchpad Mini MK3 controller to see it in the MIDI controller menu.
5. Connect your Launchpad Mini MK3 and enter Programmer Mode (see bellow how to do it).
6. Go to the DJay Pro MIDI configuration menu, select the Launchpad Mini MK3 MIDI device (not the DAW one), and choose the new configuration file from the list at the top.
**You're ready to go!**

**Setting your Launchpad Mini MK3 into Programmer Mode.**
(It’s a quick process you’ll need to do each time you power it on, but it’s no big deal once you get the hang of it.)
1. Power up your Launchpad by plugging in the USB-C cable.
2. Press and hold the *Session pad* for about 2 seconds. You’ll see the pad layout change.
3. Press the *Stop/Solo/Mute pad* on the bottom right. The LEDs on the grid should display the word “Programmer.”
4. Press the *Session pad* twice (the first one to skip the loooong text display, and the second to come back to the grid view). All the LEDs will turn off, and **your Launchpad is now ready**!

In this mode, your Launchpad will send MIDI messages when you press any of the pads and, most importantly, **it can receive RGB color commands from djay Pro** to light up the pads!

For those who want to discover more about *Programmer Mode*, here’s the link to the [Launchpad Mini [MK3] Programmer’s Reference Manual](https://fael-downloads-prod.focusrite.com/customer/prod/s3fs-public/downloads/LPP3_prog_ref_guide_200415.pdf).

### A Quick Side Note

As I’ve been using the Mixtour, which doesn’t have jog wheels, I’ve fully embraced the “SYNC user” life! As a result, this mapping is heavily tailored to support that workflow. You’ll find extensive functions for things like beat jumping, sync control, downbeat alignment, and tempo management to make mixing smooth and seamless.

### Function Mapping

Here is the general layout for the functions. This mapping reflects my personal way of using djay Pro, so feel free to adjust it to suit your needs. The good news is, you won’t have to edit the XML file to do this. djay Pro lets you modify the mapping directly within the MIDI controller configuration menu without affecting the custom Cue color settings. *Just be careful not to edit the cue-mapped functions themselves or you may overwrite the dynamic RGB color mapping.*
- The mapping on the right corresponds to the SHIFT functions. Press SHIFT + Pad simultaneously to access them.
- The FX mapping must be done inside DJay Pro (FX, instant FX, main FX) according to your preference.

<img width="1371" height="727" alt="Launchpad-mini-mk3-mapping" src="https://github.com/user-attachments/assets/47edc5ab-5b8a-4df5-8ec7-fd4491f72b16" />

### DIY: The Technics to Enable Dynamic RGB Mapping on your own configuration file
Dynamic RGB mapping allows your MIDI controller's pads to display different colors based on cue point assignments in DJay Pro, creating a more intuitive and visually organized DJ experience. 

Here’s how to proceed **if you want to add dynamic RGB mapping to an existing configuration file** by editing it:

**1. Map Cue Points in DJay Pro:** 
First, open DJay Pro's MIDI controller configuration panel and locate your controller's pad mappings. Assign each pad to its corresponding cue point function (Cue 1, Cue 2, etc.) and set a default color value for each pad. This establishes the basic connection between your physical controller and the software's cue system.

**2. Locate and Edit Configuration File:** 
Navigate to your DJay Pro configuration directory and find your controller's configuration file (typically a .plist or .xml file). Make a backup copy before editing. Open the file in a text editor to access the MIDI mapping parameters.

**3. Change Color Assignment to Default:** 
For each cue function in the configuration file, locate the color assignment parameters and change them to use default values instead of fixed colors. This allows the dynamic color system to take control of pad illumination based on the cue point colors you've set in the software.
```xml
		<dict>
			<key>keyPath</key>
			<string>turntable1.cueOrJumpIfAlreadySetCuePoint1</string> <!-- Command for CUE1 -->
			<key>midiChannel</key>
			<integer>0</integer> <!-- Identify the midi channel used by the Launchpad -->
			<key>midiData</key>
			<integer>51</integer> <!-- Identify the midi control sent by the Launchpad -->
			<key>midiMessageType</key>
			<integer>1</integer>
			<key>output</key>
			<dict> <!-- Start of the block to be replaced -->
				<key>midiMaxValue</key> 
				<real>21</real> <!-- Defining the RGB colors for the PAD when ON -->
				<key>midiMinValue</key>
				<real>31</real> <!-- Defining the RGB colors for the PAD when OFF -->
			</dict> <!-- End of the block to be replaced -->
		</dict>
```
Each CUE-related section should be edited, as shown below, to replace the fixed RGB color mapping with the default RGB color (which will depend on the UserInfo section).
```xml
		<dict>
			<key>keyPath</key>
			<string>turntable1.cueOrJumpIfAlreadySetCuePoint1</string> <!-- Command for CUE1 -->
			<key>midiChannel</key>
			<integer>0</integer>
			<key>midiData</key>
			<integer>51</integer>
			<key>midiMessageType</key>
			<integer>1</integer>
			<key>output</key>
			<dict/> <!-- Replace the RGB color mapping by this line -->
		</dict>
```
**4. Add User Info Section:** 
At the end of the configuration file, add the userInfo section with the RGB color mapping values:
```xml
	<key>userInfo</key>
	<dict>
		<key>padColorOff</key>
		<integer>0</integer>
		<key>padColorWhiteActive</key>
		<integer>3</integer>
		<key>padColorWhiteDimmed</key>
		<integer>1</integer>
		<key>padColorsActive</key>
		<array>
			<integer>5</integer>  <!-- Set the RGB color value for CUE index 1 -->
			<integer>84</integer> <!-- Set the RGB color value for CUE index 2 -->
			<integer>45</integer> <!-- Set the RGB color value for CUE index 3 -->
			<integer>13</integer> <!-- Set the RGB color value for CUE index 4 -->
			<integer>22</integer> <!-- Set the RGB color value for CUE index 5 -->
			<integer>57</integer> <!-- Set the RGB color value for CUE index 6 -->
			<integer>33</integer> <!-- Set the RGB color value for CUE index 7 -->
			<integer>51</integer> <!-- Set the RGB color value for CUE index 8 -->
			<integer>37</integer> <!-- Set the RGB color value for CUE index 9 -->
			<integer>81</integer> <!-- Set the RGB color value for CUE index 10 -->
			<integer>20</integer> <!-- Set the RGB color value for CUE index 11 -->
			<integer>32</integer> <!-- Set the RGB color value for CUE index 12 -->
			<integer>13</integer> <!-- Set the RGB color value for CUE index 13 -->
			<integer>84</integer> <!-- Set the RGB color value for CUE index 14 -->
			<integer>95</integer> <!-- Set the RGB color value for CUE index 15 -->
			<integer>94</integer> <!-- Set the RGB color value for CUE index 16 -->
		</array>
		<key>padColorsDimmed</key>
		<array>
			<integer>2</integer> <!-- Dimmed colors are not useful in this config -->
			<integer>2</integer>
			<integer>2</integer>
			<integer>2</integer>
			<integer>2</integer>
			<integer>2</integer>
			<integer>2</integer>
			<integer>2</integer>
			<integer>2</integer>
			<integer>2</integer>
			<integer>2</integer>
			<integer>2</integer>
			<integer>2</integer>
			<integer>2</integer>
			<integer>2</integer>
			<integer>2</integer>
		</array>
	</dict>
```
This configuration defines the color palette that your controller will use, with separate values for active states, enabling dynamic color changes that match your cue point assignments in real-time.
The **color code** used is tailored specifically for the Novation Launchpad to correspond with the cue colors used in DJay Pro, based on the launchpad RGB color code map:

<img width="528" height="264" alt="Launchpad-mini-mk3-pad-colors" src="https://github.com/user-attachments/assets/1c0d777c-21c2-4d2e-9a5e-1465afcd720b" />

I couldn't have done all this without the extensive information on DJay Pro's advanced XML functions that I found in the great [Github repo ](https://github.com/t0mekk/djay-pro-midi-documentation/blob/main/BEGINNER.md) by [t0mekk](https://github.com/t0mekk)

**🎧 I hope you’ll enjoy this project and config file! 🎶✨**
Feel free to reach out if you have any questions or want to share your experience. 🙌💬
