# XLook

A tweak app for the Infinix Note 11 Pro, built on Shizuku. It does for your phone what Good Lock / Fine Lock do for Samsung phones.
(Good Lock and Fine Lock only work on Samsung phones, so a copy of them would not run on an Infinix.)

## What it does

- **Display**: display size (with a 10-second "keep this?" safety check), text size, dark mode, refresh rate
- **Status bar**: battery percentage, clock seconds, hide icons
- **Behavior**: animation speed, navigation style, screen timeout, developer switches
- **Apps**: disable, remove (for your user) or restore any app. The apps the phone needs are protected.
- **Shortcuts**: one tap to system settings screens
- **Terminal**: run a shell command through Shizuku
- **Reset all tweaks**: one button puts everything back

Some Infinix software versions ignore some of these settings (refresh rate, hidden icons, navigation style). If one does nothing on your phone, that setting is the reason, not a bug in the others.

## Get the APK (you do this on your laptop, about 10 minutes)

1. Sign in at github.com. Click **New repository**. Name it `xlook`. Choose **Private**. Click **Create repository**.
2. On the new page, click **uploading an existing file**.
3. Unzip this project. Open the unzipped folder and drag **everything inside it** into the browser. This includes the `app` folder, the `.github` folder and all the loose files. Click **Commit changes**.
4. Open the **Actions** tab. Click the **Build APK** run. Wait 3 to 5 minutes for the green check.
   - If there is no run: click **Build APK** on the left, then **Run workflow**.
   - If the `.github` folder did not upload: click **Add file > Create new file**, type `.github/workflows/build.yml` as the name, and paste the text from `build-workflow.yml`.
5. Scroll to **Artifacts** at the bottom of the run. Click **XLook-apk** to download it. Unzip it. You get `app-release.apk`.
6. Send the APK to your phone and install it. Allow "Install unknown apps" when asked.

Keep the repository private. The signing key is inside the project so that new builds can update old ones.

## First start on the phone

1. Open Shizuku and start it with Wireless debugging. You repeat this after every restart.
2. Open XLook. Tap **Allow** on the Shizuku card and confirm.
3. When the card turns green, the modules unlock.

## If the build fails

Open the failed run, open the red step, and send me the last 30 lines of the log. I will fix it.

## Notes for developers

- Plain Java, no AndroidX UI libraries. The whole UI is built in code.
- One dependency: [Shizuku-API](https://github.com/RikkaApps/Shizuku-API) 13.1.5 (Apache-2.0).
- `ShellService` runs in Shizuku's user-service process as the shell user. It is a plain `Binder`, so there is no AIDL. Raise `ShellService.VERSION` when you change it.
- Ideas came from Canta (app list), Iconify and SystemUI Tuner (status bar and navigation tweaks) and the Shizuku demo (service wiring). No code was copied from them.
