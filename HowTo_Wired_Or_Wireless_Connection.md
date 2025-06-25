⚠️ **Warning: Unsupported Scan Rates & CRT Hardware Safety**

During BIOS boot-up or when using unsupported video signals (e.g., out‑of‑range horizontal scan rates), CRT can experience **hard stress** on its deflection circuitry. In some older or lower-quality CRT displays, this may result in:

- **Overheated or saturated flyback transformer**, horizontal deflection coil, or driver transistor  
- Potential **component burnout** (deflection ICs, coils, capacitors)

➡️ **To minimize risk**:
- Keep the CRT **powered off** or switched to another input during BIOS/boot sequences  
- Avoid feeding **non-CRT-safe signals** until Batocera has properly initialized safe modelines via Switchres


## 🧠 Important Information:

The reason multiple monitors cannot be connected during setup is that Batocera's current implementation of multi-screen support can interfere with detecting the correct output.  

To avoid this, all outputs except the one in use must be disabled. It's essential that the output port you use during setup is the same one you will use for CRT output. **Following this step is crucial for proper configuration.**  

That said, you can still install the script locally using an LCD/OLED monitor, but it must be connected to the same output you plan to use for the CRT.  

**Guidelines for Specific Outputs:**  
- **VGA Output:**  
  * Use a VGA-to-VGA cable to connect an LCD/OLED monitor.  
  * Alternatively, use a VGA-to-HDMI or VGA-to-DP converter.  

- **DVI-I Output:**  
  * Use a DVI-I-to-DVI-I cable to connect an LCD/OLED monitor.  
  * Alternatively, use a DVI-I-to-HDMI or DVI-I-to-DP converter.  

You may also use an EDID emulator (also known as a dummy plug or headless display adapter) for VGA, DVI-I, or DP outputs to simplify setup.

---

## 💻 Recommended Installation Method:

It’s still recommended to install the script via SSH, as it’s the quickest and most convenient method, provided the PC is connected to the same network.  

You **don’t need a second PC for this**—your mobile phone or laptop can be used with an SSH client.  

   [📎 Batocera SSH Guide](https://wiki.batocera.org/access_the_batocera_via_ssh)

**Examples of SSH clients for iOS devices:**  
- Blink Shell  
- Termius  
- a-Shell  
- WebSSH  

**Examples of SSH clients for Android:**  
- ConnectBot  
- JuiceSSH  
- Termius  
- Termux

---

## 📥 Installation

- Run the CRT Script
- Choose the correct input
- Select a correct monitor profile for your CRT
- Set resolution to 640x480/768x576  
  *(No official theme support for 320x240 at this point)*
- Set monitor rotation to "None", NORMAL (0°)  
  *(Horizontal setup = Normal)*
- Press Enter and skip ADVANCED CONFIGURATION for all 4 options  
  *(If you don't know what they mean)*
- Default resolution for GunCon2 calibration is `320x240@60Hz`

---

### 🌀 Install the CRT Script via Terminal (curl method)

**Latest version: v41**

You can install the script using **either** of the commands below.  
🟰 They are functionally identical — just different URLs pointing to the same script.

- **Option 1 – bit.ly (short link):**
  ```bash
  bash <(curl -Ls https://bit.ly/batocera-crt-script | sed 's/\r$//')
  ```

- **Option 2 – Pastebin (direct link):**
  ```bash
  bash <(curl -s https://pastebin.com/raw/iC21J0W6 | sed 's/\r$//')
  ```

- **Optional: Scan QR Code from your phone to open the script link:**

![QR Code for Mobile Installation](https://raw.githubusercontent.com/Redemp/Redemp-Batocera-CRT-Script-wiki-repository/main/wiki_page/bit.ly_batocera-crt-script_small.png)

> 🛠️ This command chain downloads the latest version, extracts its contents, moves the folder, sets script permissions, preserves backups (if any), and finally executes the script.

---

> 📌 **Don't forget:** After installing the CRT Script, check the  
[🔗 Post-Installation Steps](https://github.com/ZFEbHVUE/Batocera-CRT-Script/blob/main/HowTo_Wired_Or_Wireless_Connection.md#-post-installation-steps-important)  
to complete your setuP.

---

### 🔁 Special Instructions for R9 380 and Similar AMD GPUs

If you're using an **AMD R9 380** or similar card that doesn’t initially detect analog outputs:

1. **Run the script once** using one of the commands above.
   - This will re-enable analog output functionality (e.g., DVI-I/VGA).
   - You’ll be asked to **reboot your system** after the patch is applied.

2. **After reboot**, rerun the script again to continue with full CRT setup:
   ```bash
   /userdata/system/Batocera-CRT-Script/Batocera_ALLINONE/./Batocera-CRT-Script-v41.sh
   ```

✅ After this, you can begin setting up your CRT resolutions, display modes, and video profiles normally.

---

> 📌 **Don't forget:** After installing the CRT Script, check the  
[🔗 Post-Installation Steps](https://github.com/ZFEbHVUE/Batocera-CRT-Script/blob/main/HowTo_Wired_Or_Wireless_Connection.md#-post-installation-steps-important)  
to complete your setup.

---

## 📦 Manual Installation

Use this if installing via wired or wireless network manually.

Before running the script:
- Connect the correct output on your GPU to the correct cable.
- Ensure your CRT is either **off** or on a **different AV channel** during setup.

### Steps:

1. Press the **Code** button on GitHub and choose **Download ZIP**

2. Extract `Batocera-CRT-Script-main.zip` into a temporary folder on your PC

3. Access Batocera over your network:  
   [📎 Batocera Network File Transfer Guide](https://wiki.batocera.org/add_games_bios?s[]=transfer#add_games_bios_files_to_batocera)

4. Drag and drop the `system` folder into `/userdata`  
   *(Via SMB, you're already in `/userdata`)*

5. Connect via SSH:  
   [📎 Batocera SSH Guide](https://wiki.batocera.org/access_the_batocera_via_ssh)

6. In SSH terminal, run the following:

```
cd /userdata/system/Batocera-CRT-Script/Batocera_ALLINONE
chmod 755 Batocera-CRT-Script-v41.sh
./Batocera-CRT-Script-v41.sh
```

You'll be greeted with a welcome message.  
Press Enter and follow the onscreen instructions.

## ✅ Post-Installation Steps (Important!)

Once the installation completes, follow these steps carefully to avoid potential overlay issues and signal damage to your CRT:

### 🔌 1. Proper Shutdown After Script Installation

After installation finishes, type the following in the terminal:

```
shutdown -h now
```

This ensures Batocera saves the changes properly before powering off.  
Failing to do this may cause script installation errors due to the overlay not committing changes correctly.

Once the system has shut down completely, **power it back on to continue** with the setup.

> ⚠️ **Important for CRT users:**  
Avoid having your CRT powered on or set to the same input **during BIOS/post boot**, especially if you're using a **15kHz-only CRT**. The default output sends **unsafe 31kHz signals** during early BIOS/post boot.

---

### 🔁 2. First Boot After Installation – Setup Instructions

Once your system is rebooted **with the CRT Script installed**, you must do the following:

1. Go to:  
   `MAIN MENU → SYSTEM SETTINGS → HARDWARE`

2. Set these values:

   - **VIDEO OUTPUT:**  
     Set this to the correct connected output. There should only be one listed.

   - **VIDEO MODE:**  
     Set this based on your chosen profile:

#### For 15kHz CRT Profiles

| Output Resolution | Recommended Video Mode Setting |
|-------------------|--------------------------------|
| 640×480           | `Boot_480i 1.0:0:0 15KHz 60Hz`  |
| 768×576           | `Boot_576i 1.0:0:0 15KHz 50Hz`  |

#### For 31kHz (VGA) Profiles

| Output Resolution | Recommended Video Mode Setting |
|-------------------|--------------------------------|
| 640×480           | `Boot_480i 1.0:0:0 31KHz 60Hz`  |

> 📝 All profiles will have a `Boot_` prefix in the list.  
> 📝 Make sure the **Boot_** entry you select matches the **exact resolution** you picked during installation.

---


