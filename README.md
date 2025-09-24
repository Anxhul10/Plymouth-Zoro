## Development

### METHOD 1
1. **clone this repo at /ust/share/plymouth/themes/Plymouth-Zoro**
```
sudo git clone https://github.com/Anxhul10/Plymouth-Zoro.git /usr/share/plymouth/themes/Plymouth-Zoro
```
2. **add the theme to the default.plymouth**
```
sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/Plymouth-Zoro/zoro.plymouth 100
```

Verify that this theme is set as default:
```
sudo update-alternatives --config default.plymouth
```
#### OUTPUT
```bash 
There are 3 choices for the alternative default.plymouth (providing /usr/share/plymouth/themes/default.plymouth).

  Selection    Path                                                                     Priority   Status
------------------------------------------------------------
  0            /usr/share/plymouth/themes/bgrt/bgrt.plymouth                             110       auto mode
  1            /usr/share/plymouth/themes/bgrt/bgrt.plymouth                             110       manual mode
* 2            /usr/share/plymouth/themes/Plymouth-Zoro/zoro.plymouth            100       manual mode

Press <enter> to keep the current choice[*], or type selection number: 3
update-alternatives: using /usr/share/plymouth/themes/plymouth-test/simple-image.plymouth to provide /usr/share/plymouth/themes/default.plymouth (default.plymouth) in manual mode

```

and build a new initramfs to apply the changes

```bash
sudo update-initramfs -u -k all
```

⚠️ Plymouth draws over your desktop. Please note that you will need Terminal 2 on a different workspace to close Plymouth. ⚠️

#### Terminal 1

##### Tab 1

**Start Plymouth daemon**

```bash
sudo plymouthd --no-daemon --debug
```

##### Tab 2

**Show splash**

```bash
sudo plymouth show-splash
```
> [!NOTE]
> This will take over your screen and prevent you from running other apps until Plymouth is stopped.
> To exit, press Ctrl + Alt + F3 to switch to a virtual terminal, then run the command below.
> And to exit virtual terminal use Ctrl + Alt + F2


#### Terminal 2

With this terminal you can test the following modes and user interactions.
When you're done, you can close Plymouth

```bash
sudo plymouth quit
```
## METHOD 2

1. **COPY PLYMOUTH TO /usr/share/plymouth/themes**
```
sudo cp -r ~/path/to/plymouth /usr/share/plymouth/themes
```
3. **Run the test-script** or run ``` sudo plymouthd ; sudo plymouth --show-splash ; sleep 10 ; sudo killall plymouthd ```

Make the script executable and run it:

```bash
chmod +x run-plymouth-test.sh
./run-plymouth-test.sh
```

> [!NOTE]
> This will take over your screen while running. To switch to a virtual terminal use `Ctrl+Alt+F3`. To return to your graphical session use `Ctrl+Alt+F2` (or the > F1–F7 key your distro uses).

# Example

1. **Change directory**

```bash
cd /usr/share/plymouth/themes
```

2. **Copy theme**

```bash
sudo cp -r ~/CodeVault/github/Plymouth-Zoro .
```
