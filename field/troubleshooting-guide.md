# IDEA System — Troubleshooting Guide
_For Tapiwa — Technical Lead_

You are the first line of support on-site. This guide covers the most common problems and what to do about each one. If you cannot resolve the issue on-site, follow the escalation steps at the bottom.

---

## 1. `engine-1.local` Does Not Load

**Symptoms:** Opening Chromium and going to `engine-1.local` gives "Site can't be reached" or a blank page.

This means the engine server itself is not reachable. Check in this order:

1. **Is the server powered on?**
   - Look for a power light on the Raspberry Pi / Appdocker device
   - If off: plug it in and wait 2–3 minutes, then try again

2. **Is the WiFi network visible?**
   - On any device, look for the `appnet` network in WiFi settings
   - If not visible: the WiFi access point may be off — check its power and lights

3. **Is the device connected to the correct WiFi?**
   - Open WiFi settings — confirm it shows `appnet`, not another network

4. **Try a different device**
   - If one device cannot reach `engine-1.local` but another can: the problem is with that device, not the server — restart it

5. **Restart the server**
   - Power the Raspberry Pi off and on again (unplug and replug)
   - Wait 3 minutes, then try `engine-1.local` again

**If none of the above works:** Take a photo of the server and any lights. Post in the WhatsApp group with a description. Koen will provide remote support.

---

## 2. App Not Showing as Running on the Status Page

**Symptoms:** `engine-1.local` loads but Kolibri, Nextcloud, or Wikipedia is not shown as **Running**. Status may show: Undocked, Stopped, Starting, or Error.

| Status shown | What it means | What to do |
|---|---|---|
| Not in the list / Undocked | The app disk is not docked | Dock the correct app disk into the Appdocker — the app will start automatically |
| Starting | App is still loading | Wait 1–2 minutes and refresh the page |
| Stopped | App is docked but not running | Check if the disk is properly seated; try undocking and re-docking |
| Error | App started but encountered a problem | Note the error; post in WhatsApp group with a photo; Koen to investigate remotely |

> **The most common cause** of an app not being available is that the disk is not docked. Before assuming a technical fault, check that all app disks are physically inserted.

---

## 3. Student Cannot Log In to Kolibri

**Symptoms:** Student enters username and password but gets an error, or does not know their login.

**Check in this order:**

1. **Is the username correct?**
   - Kolibri usernames are case-sensitive — check for capital letters
   - Confirm the exact username with the teacher (they set it up in Week 1)

2. **Reset the student's password**
   - Log in with the **teacher account**
   - Go to **Class** → click the student's name → **Edit** → set a new password
   - Simple passwords work best: e.g. `student1` — tell the student the new password

3. **Student does not have an account yet**
   - Teacher needs to create it — go to **Class** → **Enroll learners** → **New user**

4. **Student account exists but is not in the class**
   - Teacher goes to **Class** → **Enroll learners** → find the student → add them

**Note:** The admin account (admin / admin911!) can also reset passwords — use this if the teacher is not available.

---

## 4. Student Cannot Log In to Nextcloud

**Symptoms:** Student enters username and password but gets an error.

**Check in this order:**

1. **Is the username and password correct?**
   - Nextcloud usernames and passwords are set by the teacher admin — confirm with the teacher
   - Try logging in yourself to test the credentials

2. **Reset the student's password**
   - Log in with the **teacher admin account** (created in Week 1)
   - Go to **top-right menu → Accounts** → find the student → click **Edit** → set a new password
   - Tell the student the new password

3. **Student does not have an account**
   - Teacher admin must create one — follow the User Registration presentation

---

## 5. Student Cannot See a Shared Folder in Nextcloud

**Symptoms:** Student logs in to Nextcloud but the shared class folder is not visible.

**Check in this order:**

1. **Is the student in the correct class group?**
   - Teacher admin goes to **Accounts → Groups** → click the class group → check the student is listed
   - If not: click **Add member** and add the student

2. **Is the folder actually shared with the group?**
   - Teacher goes to **Files** → right-click the folder → **Sharing** → check the group is listed
   - If not: add the group with at least **View** permission

3. **Try refreshing the browser**
   - Sometimes a page refresh is enough — ask the student to press F5 or reload the page

---

## 6. Kolibri Is Slow or Students Cannot Open Videos

**Symptoms:** Pages load slowly, videos buffer or do not play.

**Check in this order:**

1. **How many devices are connected?**
   - If many devices are on the network at the same time, performance may drop
   - Try limiting to one group of students at a time

2. **Is the video channel correct?**
   - Some channels contain only documents, not videos — check the channel type
   - Videos play from the channel itself, no download required

3. **Try a different resource type**
   - If videos are too slow, switch to exercises or documents for that session
   - Note the issue in the field report

4. **Restart Kolibri**
   - This is done by restarting the server (see Section 1, Step 5)
   - Wait 3 minutes after restart before trying again

---

## 7. Kolibri Reports Show No Data

**Symptoms:** You open Reports but see no student activity, even though students have been using it.

**Check:**

1. **Are students logging in with their own accounts?**
   - Reports only track activity for logged-in users — if students used the guest mode or someone else's account, no data is recorded
   - Remind students to always log in before starting a lesson

2. **Is the correct class selected?**
   - Go to **Reports → Classes** → make sure you have selected the right class

3. **Has there been enough time?**
   - Reports update as students use the system — if the session just ended, wait a few minutes and refresh

---

## 8. Nextcloud Activity Log Shows Nothing

**Symptoms:** You open the Activity log but it is empty or shows no recent logins.

**Check:**

1. **Is the Activity app enabled?**
   - Go to **top-right menu (your name) → Apps** → search for "Activity" → check it is enabled
   - If not enabled: enable it. If you cannot access Apps settings, contact Koen to enable remotely.

2. **Are you looking at the correct time range?**
   - The Activity log may default to a short period — scroll up or adjust the time filter if available

---

## Escalation — When to Call for Help

If you cannot resolve a problem on-site after following the steps above:

1. **Take a photo** of the problem — the screen, any error message, the server
2. **Write a short description:** what happened, what you tried, what the result was
3. **Post in the WhatsApp group** — Koen and Justice are following all activity
4. **Note it in the field report** — always document issues even if resolved on-site

Koen can provide remote technical support for issues he cannot resolve via WhatsApp guidance.

---

_Keep this guide with you at every visit. Update it when you discover a new fix._
