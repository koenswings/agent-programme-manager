# Installing Remote Support on the School Pis — Guide for Tapiwa

**Prepared by:** Atlas (IDEA COO)  
**Date:** 2026-03-29  
**Who this is for:** Tapiwa — field coordinator, Zimbabwe deployment

---

## What this is about

IDEA is adding a way for our technical team to help with Pi problems remotely — without
needing to travel to the school. It works using a tool called Tailscale.

**The important things to know:**

- This does not change how the Pis work day-to-day. Teachers and students will notice nothing.
- Tailscale is installed but stays dormant (sleeping). It does not use internet or run in the background.
- Remote support only activates when **you** start it, and only while you are present.
- When you press Enter to end the session, the Pi goes fully offline again. Automatically.

You need to visit each school once to install it. After that, if a problem occurs, you can
activate it during your next school visit (or a dedicated visit if urgent).

---

## What you need

1. **The USB drive** from Koen with the upgrade files on it
2. **A keyboard and screen** connected to the Pi (or use the school's setup)
3. About **10 minutes per school**

---

## Step 1 — Install the upgrade

Do this at each school Pi. You only need to do it once per Pi.

1. Insert the USB drive into the Pi
2. Open a terminal on the Pi (the black screen with a cursor)
3. Find the USB drive:
   ```
   lsblk
   ```
   You will see something like `sda1` or `sdb1` listed. Note which one is the USB.

4. Mount the USB drive (replace `sda1` with what you saw):
   ```
   sudo mkdir -p /mnt/usb
   sudo mount /dev/sda1 /mnt/usb
   ```

5. Run the install script:
   ```
   sudo bash /mnt/usb/upgrade-tailscale/install.sh
   ```

6. Wait for it to finish. You will see:
   ```
   Installation complete.
   Tailscale is installed but DISABLED — no change to normal Pi operation.
   ```

7. Unmount and remove the USB drive:
   ```
   sudo umount /mnt/usb
   ```

**That's it for the installation.** The Pi is ready for remote support next time it's needed.
Normal operation is not affected.

---

## Step 2 — Activating remote support (when IDEA staff needs access)

Only do this when Koen or IDEA technical staff ask you to. You need to be at the school.

**Before you start:** Connect the Pi to the internet. The easiest way is:
- Connect your phone to the Pi using a USB cable
- Turn on **USB tethering** on your phone (Settings → Hotspot → USB tethering)
- Or use a 4G Wi-Fi hotspot connected to the Pi via ethernet

**Then:**

1. Open a terminal on the Pi
2. Run:
   ```
   sudo /usr/local/bin/tailscale-debug-activate.sh
   ```

3. Wait about 10 seconds. You will see:
   ```
   Remote support is ACTIVE

     This Pi's address: 100.x.x.x
     Hostname:          engine-xxxxxx

     Send this address to IDEA staff now.

   Press ENTER when the support session is finished...
   ```

4. **Send the address (100.x.x.x) and the hostname to Koen** — via WhatsApp or call.
   IDEA staff will connect and start working on the Pi.

5. **Stay at the terminal.** While you wait, the cursor sits on the "Press ENTER" line.
   Do not close the terminal or turn off the screen.

6. When Koen tells you the session is finished, **press Enter**.
   You will see:
   ```
   Done. Remote support mode is OFF.
   This Pi is offline again.
   ```

7. You can now disconnect the phone/hotspot. The Pi is offline again.

---

## What if something goes wrong

**"ERROR: Tailscale not installed"**  
→ The upgrade was not done yet on this Pi. Go back to Step 1.

**"ERROR: Auth key missing"**  
→ The USB drive may have been prepared without the auth key. Contact Koen.

**The script starts but says "unknown" for the IP address**  
→ The Pi could not reach the internet. Check the phone USB tethering is on and the USB cable is connected. Then try again.

**The Pi freezes or the terminal closes**  
→ Remote support will end automatically when the connection drops. Inform Koen.
   To manually stop Tailscale: `sudo tailscale down && sudo systemctl stop tailscaled`

---

## Which Pis need the upgrade?

All Pis shipped before March 2026 need the upgrade. Pis built after that will have it
pre-installed.

Keep a record of which schools have been upgraded. Use the school visit checklist
(`field/visit-checklist.md`) to mark each Pi as done.

---

## Questions?

Contact Koen or the IDEA technical team via WhatsApp.
