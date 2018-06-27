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

### install gnu command line tools ###

Then add the following line to your .bashrc or .zshrc:
`export PATH="$(brew --prefix coreutils)/libexec/gnubin:/usr/local/bin:$PATH"`

`brew install coreutils`

``` bash
brew install binutils
brew install diffutils
brew install ed --with-default-names
brew install findutils --with-default-names
brew install gawk
brew install gnu-indent --with-default-names
brew install gnu-sed --with-default-names
brew install gnu-tar --with-default-names
brew install gnu-which --with-default-names
brew install gnutls
brew install grep --with-default-names
brew install gzip
brew install screen
brew install watch
brew install wdiff --with-gettext
brew install wget
```

In addition, some GNU command line tools already exist by default on OS X, but you may want a newer version:

``` bash
brew install bash
brew install emacs
brew install gdb  # gdb requires further actions to make it work. See `brew info gdb`.
brew install gpatch
brew install less
brew install m4
brew install make
brew install nano
```

As a complementary set of packages, the following ones are not from GNU, but you can install and use a newer version instead of the version shipped by OS X:

``` bash
brew install file-formula
brew install git
brew install openssh
brew install perl
brew install python
brew install rsync
brew install svn
brew install unzip
brew install vim --override-system-vi
brew install macvim --override-system-vim --custom-system-icons
brew install zsh
```

### uninstall google update installer ###

```
The technical details
If you’re curious what Google Update Uninstaller really does, these are the commands we run:

Local uninstallation:
python ~/Library/Google/GoogleSoftwareUpdate/GoogleSoftwareUpdate.bundle/\
Contents/Resources/GoogleSoftwareUpdateAgent.app/Contents/Resources/\
install.py --uninstall
touch ~/Library/Google/GoogleSoftwareUpdate
Global uninstallation:

sudo python /Library/Google/GoogleSoftwareUpdate/GoogleSoftwareUpdate.bundle/\
Contents/Resources/GoogleSoftwareUpdateAgent.app/Contents/Resources/\
install.py --uninstall
sudo touch /Library/Google/GoogleSoftwareUpdate
```
