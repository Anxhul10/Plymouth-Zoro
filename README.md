# OnePiece Plymouth Theme

## Installation on Ubuntu

Install the theme:

    sudo update-alternatives --install \
      /usr/share/plymouth/themes/default.plymouth \
      default.plymouth \
      /usr/share/plymouth/themes/onePiece-plymouth/onePiece-plymouth.plymouth \
      120

Select the default theme:

    sudo update-alternatives --config default.plymouth

Update the initramfs image:

    sudo update-initramfs -u

Now reboot.

Note: If you want to install this on Ubuntu versions older than 16.04,
change the path from /usr/share/plymouth to /lib/plymouth. Update the
path inside the `onePiece-plymouth.plymouth` file as well.

---

## Development

### Method 1

1. Clone this repository into `/usr/share/plymouth/themes`:

    sudo git clone <https://github.com/Anxhul10/onePiece-plymouth.git>

1. Add the theme to `default.plymouth`:

    sudo update-alternatives --install \
      /usr/share/plymouth/themes/default.plymouth \
      default.plymouth \
      /usr/share/plymouth/themes/onePiece-plymouth/onePiece-plymouth.plymouth \
      120

1. Select the theme:

    sudo update-alternatives --config default.plymouth

#### Example output

    There are 4 choices for the alternative default.plymouth
    (providing /usr/share/plymouth/themes/default.plymouth).

      Selection    Path
      Priority   Status
    ------------------------------------------------------------
      0           /usr/share/plymouth/themes/onePiece-plymouth/
                  onePiece-plymouth.plymouth   120       auto mode
      1           /usr/share/plymouth/themes/bgrt/bgrt.plymouth
                  100       manual mode
    * 2           /usr/share/plymouth/themes/onePiece-plymouth/
                  onePiece-plymouth.plymouth   120       manual mode
      3           /usr/share/plymouth/themes/spinner/spinner.plymouth
                  70        manual mode

    Press <enter> to keep the current choice[*], or type selection number:

Build a new initramfs to apply the changes:

    sudo update-initramfs -u -k all

NOTE: Plymouth draws over the desktop. Keep another terminal (TTY2)
open to stop Plymouth when testing.

#### Terminal 1 — Tab 1: Start Plymouth daemon

    sudo plymouthd --no-daemon --debug

#### Terminal 1 — Tab 2: Show splash

    sudo plymouth show-splash

Note: This will take over your screen and prevent running other apps
until Plymouth is stopped. To exit, press Ctrl+Alt+F3 to switch to a
virtual terminal, then run the command below. To return to the GUI,
press Ctrl+Alt+F2.

#### Terminal 2: Stop Plymouth when finished

    sudo plymouth quit

---

### Method 2

1. Copy the Plymouth theme to `/usr/share/plymouth/themes`:

    sudo cp -r ~/path/to/plymouth /usr/share/plymouth/themes

1. Run the test commands:

    sudo plymouthd
    sudo plymouth --show-splash
    sleep 10
    sudo killall plymouthd

Or make the script executable and run it:

    chmod +x run-plymouth-test.sh
    ./run-plymouth-test.sh

Note: This will take over your screen while running. Use Ctrl+Alt+F3
to switch to a virtual terminal. To return to your graphical session,
use Ctrl+Alt+F2 (or whichever F-key your distro uses).

---

## Example

1. Change directory:

    cd /usr/share/plymouth/themes

1. Copy theme:

    sudo cp -r ~/CodeVault/github/onePiece-plymouth .
