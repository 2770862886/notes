% Mac OSX tricks

<link id="linkstyle" rel='stylesheet' href='css/markdown.css'/>

## Shortcuts ##

### screen shot ###

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

#### tmux ####

**tmux** is a terminal multiplexer: it enables a number of terminals to be created, accessed, and controlled from a single screen.
**tmux** may be detached from a screen and continue running in the background, then later reattached.

##### Install #####

`brew install tmux`

##### Commands #####

| Command                    | Desc                        |
|----------------------------|-----------------------------|
| tmux new -s <session-name> | Start new session           |
| tmux deattach              | Detach from current session |
|                            |                             |


##### Keybindings #####

| Keybinding  | Desc                                                             |
|-------------|------------------------------------------------------------------|
| C-b         | Send the prefix key (C-b) through to the application.            |
| C-o         | Rotate the panes in the current window forwards.                 |
| C-z         | Suspend the tmux client.                                         |
| !           | Break the current pane out of the window.                        |
| "           | Split the current pane into two, top and bottom.                 |
| #           | List all paste buffers.                                          |
| $           | Rename the current session.                                      |
| %           | Split the current pane into two, left and right.                 |
| &           | Kill the current window.                                         |
| '           | Prompt for a window index to select.                             |
| (           | Switch the attached client to the previous session.              |
| )           | Switch the attached client to the next session.                  |
| ,           | Rename the current window.                                       |
| -           | Delete the most recently copied buffer of text.                  |
| .           | Prompt for an index to move the current window.                  |
| 0 to 9      | Select windows 0 to 9.                                           |
| :           | Enter the tmux command prompt.                                   |
| ;           | Move to the previously active pane.                              |
| =           | Choose which buffer to paste interactively from a list.          |
| ?           | List all key bindings.                                           |
| D           | Choose a client to detach.                                       |
| L           | Switch the attached client back to the last session.             |
| [           | Enter copy mode to copy text or view the history.                |
| ]           | Paste the most recently copied buffer of text.                   |
| c           | Create a new window.                                             |
| d           | Detach the current client.                                       |
| f           | Prompt to search for text in open windows.                       |
| i           | Display some information about the current window.               |
| l           | Move to the previously selected window.                          |
| n           | Change to the next window.                                       |
| o           | Select the next pane in the current window.                      |
| p           | Change to the previous window.                                   |
| q           | Briefly display pane indexes.                                    |
| r           | Force redraw of the attached client.                             |
| m           | Mark the current pane (see select-pane -m).                      |
| M           | Clear the marked pane.                                           |
| s           | Select a new session for the attached client interactively.      |
| t           | Show the time.                                                   |
| w           | Choose the current window interactively.                         |
| x           | Kill the current pane.                                           |
| z           | Toggle zoom state of the current pane.                           |
| {           | Swap the current pane with the previous pane.                    |
| }           | Swap the current pane with the next pane.                        |
| ~           | Show previous messages from tmux, if any.                        |
| Page Up     | Enter copy mode and scroll one page up.                          |
| Up, Down    |                                                                  |
| Left, Right |                                                                  |
|             | Change to the pane above, below, to the left, or to the right of |
|             | the current pane.                                                |
|             |                                                                  |

```



tmux new-session -s <会话名称>
tmux new -s <会话名称> 初始命令

tmux attach-session -t <会话名称>
tmux attach -t <会话名称>
tmux a -t <会话名称>

<kbd>C-b d</kbd> 分离会话

tmux new -n <窗口名>
```
|:---------------------|-------------:|
| <kbd>C-b c</kbd>     |     创建窗口 |
| <kbd>C-b [0-9]</kbd> |     切换窗口 |
| <kbd>C-b w</kbd>     |     窗口列表 |
| <kbd>C-b ,</kbd>     | 更改窗口名称 |
| <kbd>C-b &</kbd>     |     关闭窗口 |

#### ffmpeg ####
* 更改封装
`ffmpeg -i test.h264 -vcodec copy -f mp4 test.mp4`

#### 查看RGB值 ####
`Digital Color Meter`

#### Disable/Restore Sierra Gatekeeper Settings  ####
System Preference 'Security & Privacy' Allow apps downloaded from: Anywhere

``` shell
sudo spctl --master-disable
sudo spctl --master-enable
```
