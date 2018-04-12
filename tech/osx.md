% Mac OSX tricks

<link id="linkstyle" rel='stylesheet' href='css/markdown.css'/>

## Shortcuts ##

### screen shot ###

<kbd>Ctrl+Command+3/4</kbd>

### Speed up mouse speed ###

`defaults read -g com.apple.mouse.scaling`
`defaults write -g com.apple.mouse.scaling 5.0`
> and then restart computer

### Mouse Acceleration ###

`defaults write .GlobalPreferences com.apple.mouse.scaling -1`
`defaults read .GlobalPreferences com.apple.mouse.scaling`

### Stop ReportCrash service ###

`launchctl unload -w /System/Library/LaunchAgents/com.apple.ReportCrash.plist`
`sudo launchctl unload -w /System/Library/LaunchDaemons/com.apple.ReportCrash.Root.plist`

### Resume ReportCrash service ###

`launchctl load -w /System/Library/LaunchAgents/com.apple.ReportCrash.plist`
`sudo launchctl load -w /System/Library/LaunchDaemons/com.apple.ReportCrash.Root.plist`

### disable spotlight index ###

`sudo mdutil -a -i off`

### enable spotlight index ###

`sudo mdutil -a -i on`

### disable/enable System Integrity Protection ###

<kbd>Command+R</kbd> while reboot  
`crsutil enable/disable/status`  
