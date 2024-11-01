# browser-clock-overlay

## For use with a Raspberry Pi
  - Create SD card with standard Raspberry Pi OS**
  - Boot and configure Pi
    - Keyboard Layout
    - Account login
    - Connect to wifi
  - Update Pi
    - For some reason, I have to
      `sudo rm -r /var/lib/apt/lists/*`
      Then do the normal update:
    - ```
      sudo apt update
      sudo apt full-upgrade
      ```
  - Set wallpaper to black
    - Menu -> Appearance Settings -> Desktop
      - Layout -> No image      
      - Colour -> black
      - Desktop Folder -> unclick everything
    - Menu -> Appearance Settings -> Desktop
      - Theme -> Dark
  - Remove taskbar
    - `nano ~/.config/wf-panel-pi.ini`
    - Add these lines to the end
      ```
      autohide = true
      autohide_duration = 100
      heightwhenhidden=0
      ```
    - This can be a pain to undo if needed. You can ctrl-alt-F2 and login and re-edit the file to undo it
  - Edit cmdline.txt
    - `sudo nano /boot/firmware/cmdline.txt`
    - change `console=tty1` to `console=tty3`
    - after `console=tty3` add `loglevel=3 vt.global_cursor_default=0`
    - remove `splash`
    - add `logo.nologo consoleblank=1` to the end
    - Ctrl-X and save
  - Edit lightdm-gtk-greeter.conf
    - `sudo nano /etc/lightdm/lightdm-gtk-greeter.conf`
    - uncomment `background=` and make it `background=#000000`
  - Create the autostart directory
    - `mkdir ~/.config/autostart`
  - Use Chromium to download the `clock.html` and `browser.desktop` files from this repo on GitHub
  - Move `browser.desktop`
    - Open the file manager and select View -> Show Hidden Files
    - Select the downloads directory and move `browser.desktop` into `~/.config/autostart`