
# 🚀 Flash PixelExperience + OrangeFox Recovery on Redmi Note 5 Pro (Whyred)

> A complete guide to flashing PixelExperience ROM and OrangeFox recovery, rooting with Magisk, and fixing fastboot issues on Windows.

---

## 📥 Flash ROM via ADB Sideload

If you're in recovery (e.g. PixelExperience Recovery), sideload the ROM:

```bash
adb sideload PixelExperience_Plus_whyred-13.0-20230325-0421-OFFICIAL.zip
```

---

## 🚀 Flash OrangeFox Recovery via Fastboot

Reboot to fastboot mode (Vol Down + Power) and run:

```bash
fastboot flash recovery OrangeFox-R11.1_11-whyred.img
```

Reboot directly into recovery after flashing:

```bash
fastboot reboot recovery
```

---

## ❌ Fastboot Not Working? Fix It!

### Symptoms:
- `fastboot devices` shows nothing
- `< waiting for any device >`
- Phone shows "Press any key to shutdown"
- `FAILED (Write to device failed (Invalid argument))`

### ✅ Solution

Create and run this `.bat` file as Administrator:

```bat
@echo off
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\usbflags\18D1D00D0100" /v "osvc" /t REG_BINARY /d "0000" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\usbflags\18D1D00D0100" /v "SkipContainerIdQuery" /t REG_BINARY /d "01000000" /f
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\usbflags\18D1D00D0100" /v "SkipBOSDescriptorQuery" /t REG_BINARY /d "01000000" /f

pause
```

This will fix fastboot detection issues on many Xiaomi devices.

---

## 🔐 Root with Magisk (Optional)

After installing OrangeFox:

```bash
adb sideload Magisk-v27.0.zip
```

Flash via OrangeFox > Install ZIP. Then reboot to system.

---

## 📝 Example Command Flow

```bash
adb sideload PixelExperience_Plus_whyred-13.0-20230325-0421-OFFICIAL.zip
fastboot flash recovery OrangeFox-R11.1_11-whyred.img
fastboot reboot recovery
adb sideload Magisk-v27.0.zip
```

---

## 🛠 Tips

- Use latest [Platform Tools](https://developer.android.com/studio/releases/platform-tools)
- Prefer USB 2.0 ports over hubs
- Use official Xiaomi USB Drivers or Mi Flash Tool for driver fixes
- Always reboot to recovery **right after flashing it**

---

## 🤘 Contributed by: [Your Name]

If this helped you, consider giving this repo a ⭐!

