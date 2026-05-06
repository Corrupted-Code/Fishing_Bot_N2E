# Fishing_Bot O(∩_∩)O
---
Purchase access: https://funpay.com/lots/offer?id=68553922
---

## Ready-made configs are available in the beta version, no manual setup needed - see Step 9.

# 📖 User Guide - Fishing Bot

 [RU](https://github.com/Corrupted-Code/Fishing_Bot_N2E/blob/main/README.md) [EN](https://github.com/Corrupted-Code/Fishing_Bot_N2E/blob/main/README_EN.md)

---

## Step 1. Launch

Run `FishingBot.exe` **as Administrator** (right-click → "Run as administrator").

--Auto-updates will not work if the folder containing FishingBot has Cyrillic characters in the path.

> Without administrator privileges, DirectInput cannot send keystrokes to the game.

---

## Step 2. Account Login

<img width="1259" height="743" alt="image" src="https://github.com/user-attachments/assets/db06a89d-e16f-4bee-8d86-f71dd7a7ea10" />

1. Enter the **login** and **password** provided by the administrator
2. Click **Login** (or press `Enter`)
3. The bot connects to the server - you'll see the message "⏳ Connecting to server..."
4. On first login, your **HWID** (hardware identifier) is automatically bound to the account

> 🔒 If you attempt to log in from another PC — the server will block access with the error **"Account is bound to another PC"**. HWID reset is only possible through the administrator.

---

## Step 3. Main Interface

<img width="1260" height="743" alt="image" src="https://github.com/user-attachments/assets/17443c73-5891-4b07-aaba-9902fe82c026" />

The interface consists of several sections:

| Section | Purpose |
|---|---|
| **Screen Capture Zones** | Where exactly the bot monitors the ring and F button |
| **PD Controller** | Centering smoothness settings |
| **Ring Color (HSV)** | Blue ring color filter |
| **Game Window** | NTE window title for auto-focus |
| **Key Input Method** | DirectInput / SendInput / PyAutoGUI |
| **Bot Cycle** | Current step indicator |
| **Log** | All events with timestamps |

---

## Step 4. Capture Zone Setup

<img width="360" height="206" alt="image" src="https://github.com/user-attachments/assets/923d4e70-7956-4d1c-9271-64597757d669" />

The bot captures two screen areas:

### Bar Zone (top of screen)
Horizontal bar with marker, appears after a bite:

<img width="1029" height="211" alt="image" src="https://github.com/user-attachments/assets/185665be-4aaa-4489-a6d5-28ca606c2418" />

- Set the **"Bar: left / top / width / height"** sliders to cover only this bar
- Typical values for Full HD (1920×1080): `left=0.32, top=0.06, width=0.36, height=0.02`

### F Button Zone
Round hook button in the bottom right corner:

<img width="144" height="142" alt="image" src="https://github.com/user-attachments/assets/2fe39098-5250-4c46-957a-4cc7a1795539" />

- Set the **"Button: left / top / width / height"** sliders to this button area
- Typical values: `left=0.89, top=0.85, width=0.07, height=0.10`

> 💡 Use the preview on the left side of the interface - it shows in real-time what the bot is capturing.

---

## Step 5. Ring Color Setup (HSV)

The fishing ring looks like this:

<img width="127" height="137" alt="image" src="https://github.com/user-attachments/assets/798037cc-b254-49d5-a66b-dcc8331f62d1" />

This is a blue/cyan ring with a white center. The bot looks for this specific color.

### How to configure:

1. Click the **"Picker - click on the ring"** button when the ring glows blue, the picker will capture the current image
2. Click the mouse a couple of times on different points of the ring in the picker
3. The bot will automatically fill in the H, S, V values
4. Click **"Set this color as reference"** and **"Apply"**
5. Click **"Check"** - debug output will appear in the log:

<img width="489" height="516" alt="image" src="https://github.com/user-attachments/assets/36b10f4b-172c-4ee1-9ddc-9b3512309330" />

Lines showing `matched: x/x` and `→ Bite detected` mean the color is configured correctly.

---

## Step 6. Yellow Picker Setup

1. Enter fishing mode and wait for the yellow bar
2. Click on the yellow picker and select a point at the center of the yellow bar as shown in the screenshot
3. Click apply

<img width="893" height="398" alt="image" src="https://github.com/user-attachments/assets/9f84b3df-70ba-43f9-8225-baa4879a3edb" />

---

## Step 7. PD Controller Setup

The PD controller manages A/D key presses to center the marker on the bar.

| Parameter | Recommendation |
|---|---|
| **Min Peak Matches** | `2` - sufficient, increase for false positives |
| **Yellow Threshold** | `40` - pixels to determine the danger zone |
| **Dead Zone** | `8` - pixels from center where no input is sent |
| **KP (proportional)** | `0.60` - reaction strength |
| **KD (differential)** | `0.05` - dampening, eliminates jerking |
| **Bar Delay** | `1.8` s - wait time for bar to appear after bite |
| **Catch Delay** | `1.2` s - delay for LMB + F click after completing the mini-game |

---

## Step 8. Key Input Method Selection

In the **"Key Input Method"** section:

- **Auto** - bot automatically selects the best method (recommended)
- **SendInput / DirectInput** - best option for fullscreen games, requires administrator privileges
- **keybd_event (WinAPI)** - outdated but widely compatible
- **PyAutoGUI** - simplest, doesn't require privileges, but may not work in games with anti-cheat

> For NTE, **SendInput / DirectInput** is recommended.

---

## Step 9. Starting the Bot

1. Enter the game, approach a body of water and start fishing manually
2. When the fishing interface appears:

<img width="1919" height="1079" alt="ribalka" src="https://github.com/user-attachments/assets/54ea29e6-7d22-4d19-b86a-99166abb1258" />

3. Switch to the bot window and click **▶ START** (or press `F6`)
4. The cycle repeats automatically

---

## Step 10. Cloud Configs

Cloud configs are already available in the beta version - go to the configs tab in the program and select the config that matches your resolution

<img width="1259" height="739" alt="image" src="https://github.com/user-attachments/assets/9723bfd6-eb26-4424-9fc3-740b9cb2af43" />

## Common Issues

### Application Launch Errors

- Install/update:
- [WebView2 Runtime](https://msedge.sf.dl.delivery.mp.microsoft.com/filestreamingservice/files/f67cc405-2a0b-4df8-b641-023a0ee89f01/MicrosoftEdgeWebView2RuntimeInstallerX64.exe)
- [Microsoft Visual C++ Redistributable (2015-2022)](https://aka.ms/vs/17/release/vc_redist.x64.exe)

### Bot doesn't detect the ring
- Check the F button zone - it must precisely target the hook button
- Verify HSV color using the **"Check"** button - look for `matched: 0/4` in the log
- Try increasing ±dH, ±dS, ±dV

### Bot jerks the rod too sharply
- Decrease **KP** (e.g., from 0.60 to 0.40)
- Increase **KD** (e.g., from 0.05 to 0.10)
- Increase **Dead Zone** to 10–15

### Keys don't work in game
- Make sure you ran the `.exe` **as administrator**
- Change input method to **SendInput / DirectInput**
- Game window must be active (not in background)

### Error "Account is bound to another PC"
- Contact the seller to reset HWID through the server panel

### Error "Server unavailable"
- Contact the seller

---

## Tips

- 🎯 Configure zones carefully on first launch - this determines 90% of stability
- 🌅 HSV ring color may vary at different times of day in the game - adjust for your location
- 📊 Keep the log open on first launch - it will show all issues
- 💾 Settings are saved automatically in `fishing_bot_settings.json`

**Happy fishing!)**
