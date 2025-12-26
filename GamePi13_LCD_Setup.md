# GamePi13 LCD Setup (Fresh RetroPie Build)

This guide walks you through setting up the Waveshare GamePi13 1.3" LCD on a fresh RetroPie Buster 4.8.9 installation.  
It covers display only; audio and buttons can be configured later.

---

## Step 0 — Prepare a Fresh RetroPie Install

1. Flash a fresh RetroPie Buster 4.8.9 image to your microSD card.
2. Boot the Pi and complete the initial setup:
   - Configure **keyboard**
   - Configure **Wi-Fi / SSH**
   - Set **WLAN country**
3. Do **not** run any updates yet; keep the system fresh.

---

## Step 1 — Install Required Packages

Open SSH or terminal and run:

```bash
sudo apt update
sudo apt install cmake g++ git -y
This ensures you have cmake and the compiler needed to build fbcp-ili9341.

Step 2 — Download Waveshare’s Precompiled fbcp for GamePi13 (Recommended)
This is the most reliable method to get the LCD working:

bash
Copy code
cd ~
wget https://files.waveshare.com/wiki/GamePi13/Doc/Gamepi13_fbcp.zip
unzip Gamepi13_fbcp.zip
cd Gamepi13_fbcp/build
sudo chmod +x *
sudo ./fbcp-ili9341
The LCD should light up and mirror the HDMI display.

If successful, continue; otherwise troubleshoot connections and pins.

Step 3 — Configure HDMI Framebuffer
Edit /boot/config.txt to set resolution for the LCD:

bash
Copy code
sudo nano /boot/config.txt
Add the following lines at the bottom of the file:

ini
Copy code
hdmi_force_hotplug=1
framebuffer_width=320
framebuffer_height=240
Save (Ctrl + O) and exit (Ctrl + X).

Step 4 — Test the LCD
Run:

bash
Copy code
sudo ./fbcp-ili9341
The LCD should now display your RetroPie interface.

Press keyboard buttons to verify responsiveness.

If everything works, proceed to remove the big HDMI display if desired.

Step 5 — Optional: Remove Big HDMI
Power down the Pi.

Disconnect the big HDMI display.

Power on the Pi.

The LCD should remain on and functional.

Step 6 — Verify & Document
Check that the LCD mirrors RetroPie correctly.

Make note of all tested commands and configuration changes.

Save this Markdown file for future Pi builds to duplicate the setup reliably.

✅ Success
Both LCD and system are functional.

Display rotates correctly and responds to input.

Ready for next steps: audio configuration, button setup, and theme customization.

Notes:

This guide is repeatable on multiple Pi/GamePi13 setups.

Use the precompiled fbcp as it’s the most reliable for RetroPie Buster 4.8.9.

All commands are safe on a fresh install.

yaml
Copy code

---

### ✅ How to use this

1. Open VS Code.
2. Open a new file.
3. Paste the entire content above.
4. Save as:

GamePi13_LCD_Setup.md

vbnet
Copy code

5. Press `Ctrl + Shift + V` to preview and confirm:
   - Big bold headings
   - Code blocks properly shaded
   - Numbered steps clear and readable