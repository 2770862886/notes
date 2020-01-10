% Mac OSX tricks

<link id="linkstyle" rel='stylesheet' href='css/markdown.css'/>

System Shortcuts
================

### screenshot ###

<kbd>Ctrl+Command+3/4</kbd>

`defaults write com.apple.screencapture location /Users/liangchao/Desktop/sreenshots`

### 6 ways Force Quit ###

1. 
<kbd>Cmd + Opt + ESC</kbd>
2. 
<kbd>Cmd + Opt + Shift + ESC</kbd>
3. From Dock, right click

4. From Apple Menu

5. Use Activity Monitor

6. Using the terminal & kill command
`killall [processname]`
`kill -9 [pid]`

Common Commands
===============

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
`csrutil enable/disable/status`

### coreaudiod makes high cpu ###

``` shell
sudo launchctl unload /system/library/launchdaemons/com.apple.audio.coreaudiod.plist
sudo rm -r /Library/Preferences/Audio/
sudo mkdir /Library/Preferences/Audio
sudo chown -R _coreaudiod:admin /Library/Preferences/Audio
sudo launchctl load /system/library/launchdaemons/com.apple.audio.coreaudiod.plist
```

### UserEventAgent high cpu ###

``` shell
cd /System/Library/UserEventPlugins 
sudo mv com.apple.cts.plugin com.apple.cts.plugin.disabled 
sudo shutdown -r now
```

### install gnu command line tools ###

Then add the following line to your .bashrc or .zshrc:
`export PATH="$(brew --prefix coreutils)/libexec/gnubin:/usr/local/bin:/usr/local/sbin:$PATH"`

``` bash
brew install coreutils
brew install binutils
brew install diffutils
brew install ed
brew install findutils
brew install gawk
brew install gnu-indent
brew install gnu-sed
brew install gnu-tar
brew install gnu-which
brew install gnutls
brew install grep
brew install gzip
brew install screen
brew install watch
brew install wdiff
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

### install emacs with home brew ###
```
brew tap railwaycat/emacsmacport
brew install emacs-mac
ln -s /usr/local/opt/emacs-mac/Emacs.app /Applications/
ln -s /usr/local/opt/emacs-mac/bin /Applications/Emacs.app/Contents/MacOS/
```

### install iterm and oh-my-zsh and plugins ###

Install iTerm2 from the official website. [www.iterm2.com](iTerm2)

```
brew install autojump
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
git clone git://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
```

### ffmpeg ###

* 更改封装
`ffmpeg -i test.h264 -vcodec copy -f mp4 test.mp4`

### 查看RGB值 ###

`Digital Color Meter`

### Disable/Restore Sierra Gatekeeper Settings ###

System Preference 'Security & Privacy' Allow apps downloaded from: Anywhere

``` shell
sudo spctl --master-disable
sudo spctl --master-enable
```

Common Applications
===================

Quiver
------

### Shortcuts ###

* UI Navigation

    | Action                                    | Keybinding     |
    |:------------------------------------------|----------------|
    | Notebooks view                            | <kbd>C-1</kbd> |
    | Tags view                                 | <kbd>C-2</kbd> |
    | Three Panes View                          | <kbd>M-3</kbd> |
    | Two Panes View                            | <kbd>M-2</kbd> |
    | Single Pane View                          | <kbd>M-1</kbd> |
    | Toggle between three and single pane view | <kbd>M-0</kbd> |
    | Switch to 'Editor Only' mode              | <kbd>M-4</kbd> |
    | Switch to 'Preview Only' mode             | <kbd>M-5</kbd> |
    | Switch to 'Side-by-Side Preview'          | <kbd>M-6</kbd> |

* Cell Operations

    | Action                           | Keybind              |
    |:---------------------------------|----------------------|
    | New Cell                         | <kbd>S-Enter</kbd>   |
    | New Cell Above                   | <kbd>S-C-Enter</kbd> |
    | New Cell At Course               | <kbd>S-C-Pipe</kbd>  |
    | Split Cell                       | <kbd>A-M-Enter</kbd> |
    | Cut Cell                         | <kbd>S-M-x</kbd>     |
    | Copy Cell                        | <kbd>S-M-c</kbd>     |
    | Past Cell                        | <kbd>S-M-v</kbd>     |
    | Delete Cell                      | <kbd>S-M-k</kbd>     |
    | Convert to Text Cell             | <kbd>A-M-1</kbd>     |
    | Convert to Code Cell             | <kbd>A-M-2</kbd>     |
    | Convert to Markdown Cell         | <kbd>A-M-3</kbd>     |
    | Convert to LaTeX Cell            | <kbd>A-M-4</kbd>     |
    | Convert to Diagram Cell          | <kbd>A-M-5</kbd>     |
    | Move Cell Up                     | <kbd>A-M-Up</kbd>    |
    | Move Cell Down                   | <kbd>A-M-Down</kbd>  |
    | Move Cursor to start/end of Cell | <kbd>M-Up/Down</kbd> |

* Formating Operations

    | Action                 | Keybinding          |
    |:-----------------------|---------------------|
    | Show Fonts             | <kbd>M-T</kbd>      |
    | Headings               | <kbd>C-S-1..6</kbd> |
    | Paragraph              | <kbd>C-S-0</kbd>    |
    | Increase Heading Level | <kbd>C-S-]</kbd>    |
    | Decrease Heading Level | <kbd>C-S-[</kbd>    |
    | Bold                   | <kbd>M-b</kbd>      |
    | Italic                 | <kbd>M-i</kbd>      |
    | Underline              | <kbd>M-u</kbd>      |
    | Strikethrough          | <kbd>C-S-s</kbd>    |
    | Hightlight             | <kbd>C-S-h</kbd>    |
    | Inline Code            | <kbd>C-S-k</kbd>    |
    | Insert/Edit Link       | <kbd>M-K</kbd>      |
    | Insert/Edit Image      | <kbd>C-S-I</kbd>    |
    | Insert TODO            | <kbd>C-S-T</kbd>    |
    | Insert Horizontal line | <kbd>C-S-R</kbd>    |
    |                        |                     |

* Global Hotkeys

    | Action           | Keybindin          |
    |:-----------------|--------------------|
    | Search in Quiver | <kbd>C-S-M-f</kbd> |

Anki
----

[Anki China Manual](http://www.ankichina.net/anki20.html)
