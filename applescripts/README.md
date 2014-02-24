Applescripts
======================

#Collection of Applescripts

## ToggleAudioOutputAirplay
Simple Applescript to toggle between "Internal Speakers" of your Mac and external Airplay device
Note: If your Airplay device name does not start with "Zeppelin", just change the string in line 9 to the name of your device
```applescript
tell application "System Preferences"
	reveal anchor "output" of pane id "com.apple.preference.sound"
	tell application "System Events"
		tell process "System Preferences"
			-- if "Internal Speakers"
			if selected of row 1 of table 1 of scroll area 1 of tab group 1 of window "Sound" then
				set newOut to "Zeppelin"
			else
				set newOut to "Internal"
			end if
			select (row 1 of table 1 of scroll area 1 of tab group 1 of window "Sound" whose value of text field 1 starts with newOut)
		end tell
	end tell
	tell application "System Preferences" to quit
end tell
```