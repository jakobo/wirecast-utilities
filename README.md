# Wirecast AppleScript Utilities

This is a small collection of effects in Wirecast to show off some of the scripting that can be done. Specifically, it will allow you to use a utility like BetterTouchTool or Quadro to control wirecast with a semi-intuitive interface.

# SETUP
You must have a blank layer in all 5 master layers:
```
TRANSITIONS in Master Layer 1
UPPER THIRDS in Master Layer 2
LOWER THIRDS in Master Layer 3
CAMERAS in Master Layer 4
AUDIO in Master Layer 5
```

This follows most Wirecast setups. You're welcome to let these layers mean other things, just change the references here in the script.

To invoke this, run the following command from any utility's "run applescript" command. (You can also execute `oascript` directly if your tool has a command for running shell scripts.

```
do shell script "osascript <path/to>/utilities.scpt <command> <args...>"
```

# Commands
## stinger
`utilities.scpt stinger 'My Transition' 'slow', 2, 'My New Camera', 0.3, 'My Audio'`
> Used to create a "stinger" transition. It will begin by playing the transition_name, and after the first delay, will change the camera source, ideally cutting while the camera source is hidden behind the transition. It will then fade the audio back in after a second delay.

parameter | type | description
:--- | :--- | :---
transition_name | string | The name of the shot on the TRANSITION layer to use as a stinger
speed | enum string | The transition speed. One of: {slowest, slow, normal, fast, fastest}
camera_delay | float | delay in seconds before changing the camera layer
camera_name | string | The shot on the CAMERA layer to change to
audio_duration | float | _optional_ delay in seconds before changing the audio layer
audio_name | string | _optional_ audio layer to change to (if not set, audio layer will not mute)

## break
`utilities.scpt break 'BRB' 'mute'`
> Used to create BRB events or other transitional elements you do not plan to do a camera switch underneath. Can be used for automating replays, program-holding messages, etc. Will put up a system notification on OSX that lets you know it left your transition up (when using full screen transitions).

parameter | type | description
:--- | :--- | :---
transition_name | string | The name of the shot on the TRANSITION layer to use
mute_audio | enum string | Should the audio mute. One of {"", mute}


## upper
`utilities.scpt upper 'My Upper Third Shot'`
> Used to trigger a shot on the "UPPER THIRDS" layer

parameter | type | description
:--- | :--- | :---
upper_name | string | name of the shot on the UPPER THIRDS layer to change to

## lower
`utilities.scpt lower 'My Lower Third Shot'`
> Used to trigger a shot on the "LOWER THIRDS" layer

parameter | type | description
:--- | :--- | :---
lower_name | string | name of the shot on the LOWER THIRDS layer to change to

## camera
`utilities.scpt camera 'New Camera' 'fastest'`
> Used to change the shot on the CAMERAS layer at the specified speed

parameter | type | description
:--- | :--- | :---
camera_name | string | name of the shot on the CAMERAS layer to change to
speed | enum string | The transition speed. One of: {slowest, slow, normal, fast, fastest}

## audio
`utilities.scpt audio 'New Audio Mix'`
> Used to trigger a shot on the "AUDIO" layer

parameter | type | description
:--- | :--- | :---
audio_name | string | name of the shot on the AUDIO layer to change to
