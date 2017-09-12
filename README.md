Wirecast AppleScript Utilities

This is a small collection of effects in Wirecast to show off some of the scripting that can be done. Specifically, it will allow you to use a utility like BetterTouchTool or Quadro to control wirecast with a semi-intuitive interface.

```
# WIRECAST UTILITIES
# ###
# This is a utility .scpt designed to be called using any
# tool that can execute applescript. Quadro, BetterTouchTool,
# KeyboardMaestro, and many others have this functionality.
#
# As of OSX 10.4, you can pass arguments to AppleScript, and
# that is how we build a rich AppleScript for controlling
# Wirecast.
#
# SETUP
# ###
# You must have a blank layer in all 5 master layers:
# TRANSITIONS in Master Layer 1
# UPPER THIRDS in Master Layer 2
# LOWER THIRDS in Master Layer 3
# CAMERAS in Master Layer 4
# AUDIO in Master Layer 5
#
# This follows most Wirecast setups. You're welcome to let these
# layers mean other things, just change the references here in
# the script.
#
# To invoke this, run the following command from any utility's
# "run applescript" command. (You can also execute "oascript"
# directly if your tool has a command for running shell scripts.
#
# do shell script "osascript <path/to>/utilities.scpt <command> <args...>"
#
# The available commands (and their arguments) are:
#
# stinger
# Used to create a "stinger" transition. It will begin by playing the
# transition_name, and after the first delay, will change the camera
# source, ideally cutting while the camera source is hidden behind the
# transition. It will then fade the audio back in after a second delay.
#	transition_name<s>	- The name of the transition layer to use as a stinger
# 	speed<s>			    - The transition speed One of: {slowest, slow, normal,
#                       fast, fastest}
# 	camera_delay<i>		- delay in seconds before changing the camera layer
#	camera_name<s>		  - camera layer to change to
#	audio_duration<i>		- delay in seconds before changing the audio layer
#	audio_name<s>		    - audio layer to change to (if not set, audio will
#                       not mute)
#
# upper
# Used to trigger a shot on the "UPPER THIRDS" layer
#	upper_name<s>		    - name of the upper 3rd to play
#
# lower
# Used to trigger a shot on the "LOWER THIRDS" layer
# 	lower_name<s>		  - name of the lower 3rd to play
#
# camera
# Used to change the shot on the CAMERAS layer at the specified speed
#	camera_name<s>		  - name of the camera shot to play
#	speed<s>			      - The transition speed One of: {slowest, slow, normal,
#                       fast, fastest}
#
# audio
# Used to change the audio source on the AUDIO layer
#	audio_name<s>		    - The name of the audio track to switch to
```
