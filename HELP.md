# Help for the QLabFB module

What does QLab do?
QLab makes it simple to create intricate designs of light, sound, and video, which you play back during a live performance.
QLab allows you to lock in exactly how you want the light, sound, and video to play during your performance. When you are done designing, switch to “show mode” and run your show just by pressing “GO”.

The software is available at [QLab.app](qlab.app). You can use QLab for 2 channel audio and 1 screen video without
needing a license.

This module adds a TCP mode option to the *QLab* module.
Due to the nature and volume of information feedback and variables are only available in TCP mode.
This may cause a noticible increase in network traffic.

This module is intended for QLab4. While QLab3 is detected, some features may not work.

## Configuration
Setting | Description
-----------------|---------------
**Target IP** | Enter the address of the QLab computer. You can enter 127.0.0.1 if Companion is running on the same computer.
**Use TCP?** | Check to enable TCP mode. This is required for variables and feedback.
**Use Tenths** | If checked, the variable *r_left* will display 0.1 seconds when less than 5 seconds. If unchecked, the time left will be adjusted by 1 second for a more accurate count-down.
**OSC Passcode** | Enter a passcode if needed for the QLab workspace.
**Workspace** | Enter the workspace title or ID to control a specific QLab workspace, enter 'default' or leave blank to control active/default workspace.
**Specific Cue List** | Dropdown selection to limit control to a specific cuelist.

## Actions
Action | Description
-----------------|---------------
**Go** | Tell the current cue list of the given workspace to GO.
**Stop** | Stop playback but allow effects to continue rendering. e.g., playback stops, but reverbs decay naturally.
**Panic** | Tell the workspace to panic. A panic is a brief gradual fade out leading into a hard stop. A double panic will trigger an immediate hard stop.
**Panic In Time** | Tell the workspace to panic over time specified.
**Reset** | Reset the workspace. Resetting stops all cues, returns the playhead to the top of the current cue list, and restores any temporary changes made to cues (such as retargeting via a Target cue or adjustments using a "live" OSC method.)
**Next** | Move the selection down one cue.
**Previous** | Move the selection up one cue.
**Pause** | Pause all currently running cues in the workspace.
**Resume** | Un-pause all paused cues in the workspace.
**Preview** | Preview the selected cue without moving the Playhead.
**Toggle Pause** | Pause/Unpause selected cue
**GoTo (Cue/ID)** | Move the playhead to (Cue/ID). Does not start the cue.
**Start (Cue/ID)** | Start (Cue/ID). Does not move the playhead. If the specified cue is playing, this command has no effect.
**Stop (Cue/ID)** | Stops (Cue/ID) if Playing. Does not move the playhead.
**Panic (Cue/ID)** | Panic (Cue/ID) if Playing. Does not move the playhead.
**Panic (Cue/ID) In Time** | Panic (Cue/ID) over time specified if Playing. Does not move the playhead.
**Show Mode** | Enable for Show Mode, Disable for Edit Mode.
**Audition Window** | Show or Hide the Audition Window.
**Override Window** | Show or Hide the Override Controls Window.
**Master Override** | Set Master override for Midi, MSC, SysEx, OSC, Timecode, Art-Net On or Off
**Set Minimum Go** | Sets the time for double-GO protection
**Increase Prewait** | Increases the prewait time by given time for the selected cue.
**Decrease Prewait** | Decreases the prewait time by given time for the selected cue.
**Increase postwait** | Increases the postwait time by given time for the selected cue.
**Decrease postwait** | Decreases the postwait time by given time for the selected cue.
**Increase duration** | Increases the duration time by given time for the selected cue.
**Decrease duration** | Decreases the duration time by given time for the selected cue.
**Increase Start Time** | Increases the Start Time by given time for the selected cue.
**Decrease Start Time** | Decreases the Start Time by given time for the selected cue.
**Increase End Time** | Increases the End Time by given time for the selected cue.
**Decrease End Time** | Decreases the End Time by given time for the selected cue.
**Set/Unset Infinite Loop** | Set / Unset the Infinite Loop property of the selected cue.
**Set/Unset Hold last frame** | Set / Unset the Hold last frame property of the selected cue.
**Set/Unset Arm** | Set / Unset the Arm property of the selected cue.
**Set/Unset Autoload** | Set / Unset the Autoload property of the selected cue.
**Set Continue Mode** | Sets the continue mode of the selected cue.
**Set Cue Color** | Sets the color of the selected cue.
**Copy Unique Cue ID** | Copies the Unique ID of the cue at the Playhead to actions and feedbacks.
The next action or feedback inserted will have the Unique ID already filled in.

There are presets included for most of these actions.\
Show Mode, Audition Window, Arm, and Autoload actions also have a Toggle option to invert the current setting of the cue.\
For additional actions please raise a feature request at [github](https://github.com/bitfocus/companion-module-qlab-advance/issues)

## Variables available (TCP mode only)
Variable | Description
-----------------|---------------
**$(INSTANCENAME:q_ver)** | Version of QLab attached
**$(INSTANCENAME:n_id)** | UniqueID of the current Playhead Cue
**$(INSTANCENAME:n_name)** | Name of the current Playhead Cue or [none]
**$(INSTANCENAME:n_num)** | Number of the current Playhead Cue
**$(INSTANCENAME:n_notes)** | First 20 characters of the Note on the Playhead Cue
**$(INSTANCENAME:n_stat)** | Playhead Cue Status: "✕" if broken, "⏽" if loaded, "⏵" if running, "⏸" if paused, otherwise "·"
**$(INSTANCENAME:r_id)** | UniqueID of the current Running Cue
**$(INSTANCENAME:r_name)** | Name of the current Running Cue or [none]
**$(INSTANCENAME:r_num)** | Number of the current Running Cue
**$(INSTANCENAME:r_stat)** | Running Cue Status: "✕" if broken, "⏽" if loaded, "⏵" if running, "⏸" if paused, otherwise "·"
**$(INSTANCENAME:r_hhmmss)** | Remaining time for Running Cue as "HH:MM:SS"
**$(INSTANCENAME:r_hh)** | Hours left for Running Cue
**$(INSTANCENAME:r_mm)** | Minutes left for Running Cue
**$(INSTANCENAME:r_ss)** | Seconds left for Running Cue
**$(INSTANCENAME:r_left)** | Shortest display time left for Running Cue. Shows .1 increments if tenths option set.
**$(INSTANCENAME:q_{num}_name)** | Name of the QLab cue number {num}. See below for certain restrictions.
**$(INSTANCENAME:id_{ID}_name)** | Name of the QLab cue ID {ID}. See below for certain restrictions.
**$(INSTANCENAME:min_go)** | Current value of double-go protection (in seconds)

To use these, replace INSTANCENAME with the name of your module instance.

## Feedback available (TCP mode only)
Feedback | Description
-----------------|---------------
**Playhead Cue Color as Background** | Sets the button backgound to QLab color of the current playhead cue
**Running Cue Color as Background** | Sets the button background to QLab color of the currently running cue
**Cue Number Color as Background** | Sets the button background to QLab color of a specified cue
**Colors for GO status** | Set the button color for the GO button state: active or disabled via the double-go timer
**Indicate Workspace Mode** | Set the button to indicate the QLab workspace mode: Audition (window on), Show Mode, Edit Mode
**Indicate Override Window On** | Set the button to indicate Override Window is Visible
**Indicate Master Override** | Set the button to indicate if the selected Override is Active (Turned off)
**Show Cue # is Running** | Set the button to show when a specific cue is running
**Show Cue ID is Running** | Set the button to show when a specific cue ID is running

## OSC
This module connects to QLab on port 53000.

From QLab preferences OSC controls tab make sure you have the "Use OSC controls" checkbox ticked.
![QLab](images/qlab.jpg?raw=true "QLab")

### Running cue examples
 QLab can run many cues at the same time while Stream Deck has a limited number of buttons visible at once. So which *one* cue is the most useful to show on a button? This module looks for the most recently run (GO) cue and favors *run all at once* Group cues over other types of cues.

- Using a video show... 5 slide cues overlap to build a final image. After 5 'GO's all 5 cues are 'Running' resulting in a 5 picture overlay. The last 'GO' cue in the sequence will be the 'Running' cue.
- Now add 2 more screens with more images. Each transition (1 image for each screen) is now placed in a *run all* Group cue for list management. After the 5 group cues are run, QLab will show 20 cues active, 5 slides for each screen plus the 5 group cues. The last 'GO' **Group** cue will be the 'Running' cue.
- If the last 'GO' Group cue is *enter then run each*, the most recent 'GO' cue in the group will be the 'Running' cue.

### Cue Numbers / IDs
QLab allows almost any characters in a Cue Number. Some characters don't play well with OSC or Companion. Using '$', '(', or ')' in your Cue Number won't work if you want to use the `q_{num}_name` variable or the `q_bg` feedback.\
Transport actions, variables, and feedbacks have an ID version that uses the QLab Unique Cue ID as the target instead of the Cue Number. QLab does not show this internal ID so there is a special action **Copy Unique Cue ID** that will temporarily insert the ID of the playhead/selected cue into the ID style actions. \
The examples and descriptions use {num} as a place marker for the Cue or ID to use.\
Do not enter the braces {}: To refer to Cue #10 you would enter `q_10_name`.
