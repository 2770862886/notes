Mac OSX tricks
======

# Speed up mouse speed
defaults read -g com.apple.mouse.scaling
defaults write -g com.apple.mouse.scaling 5.0
and then restart computer

# Mouse Acceleration
defaults write .GlobalPreferences com.apple.mouse.scaling -1
defaults read .GlobalPreferences com.apple.mouse.scaling
