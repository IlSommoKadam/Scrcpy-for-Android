# Pull Request — Mirroring reliability, Android 14+ support, and UX improvements

## Summary

This PR proposes a set of improvements developed on the fork [IlSommoKadam/ScrcpyForAndroid](https://github.com/IlSommoKadam/ScrcpyForAndroid), focused on mirroring reliability, Android 14+ compatibility, user experience, and diagnostics.

**12 commits** · **38 files** · **+2534 / −391 lines**

## Main changes

### Mirroring reliability fixes
- Fixed black screen caused by incorrect `Surface` timing (wait for `SurfaceHolder` callback before starting the service)
- Automatic surface re-bind on resume and configuration changes
- Fixed skipped CONFIG frames after rotation: SPS/PPS parsing always active
- Encoder no longer restarted unnecessarily after the first frame (eliminates lag)

### Android 14+ and encoder
- Automatic fallback between hardware encoders when the primary fails
- Scaled touch mapping for different client and server resolutions
- Improvements to `ScreenEncoder`, `ScreenCapture`, and system wrappers

### Auto resolution
- New **Auto** mode: computes the minimum between local and remote display via ADB (`wm size`)
- `ResolutionHelper` with UI preview and active limit indication
- Localized strings EN/JA/ZH

### Rotation during session
- Rotatable mirror with `FULL_SENSOR` without disconnection
- Portrait/landscape layout reinflate with `layout-land` resources
- Video surface rebind on rotation without restarting the scrcpy service

### Device controls and status
- Online/offline LED next to the IP field (ADB connectivity check)
- ADB reboot button (`adb reboot`) with confirmation dialog
- ADB power-off button (`adb reboot -p`) with confirmation dialog
- Power button in the mirror navigation bar

### Diagnostics
- `SessionLog`: session log reset on every app start, shareable via email/WhatsApp
- `LogFileProvider` for secure log file sharing

### UI
- Styled app title with subtitle
- Expandable/collapsible settings panel
- Advanced options: video codec, max FPS, custom encoder

## Files touched

<details>
<summary>Full list (38 files)</summary>

**Client:** `MainActivity.java`, `Scrcpy.java`, `Options.java`, `VideoDecoder.java`, `ResolutionHelper.java`, `SessionLog.java`, `AdbHelper.java`, `ExecUtil.java`, layout XML, strings EN/JA/ZH

**Server:** `ScreenEncoder.java`, `ScreenCapture.java`, `Device.java`, `Options.java`, `DisplayManager.java`, `InputManager.java`, `SurfaceControl.java`

</details>

## Testing

- Local network mirroring with Auto and fixed resolution
- Client device rotation during active session
- Mirror navigation buttons (back, home, menu, power)
- ADB reboot and power-off commands
- Status LED with valid/invalid IP

## Notes

- Some UI strings in the default `strings.xml` are in Italian; they can be converted to English if preferred.
- `versionCode`/`versionName` incremented in the fork (1.5.20 / r33); final numbering at maintainer's discretion.
- No new external dependencies.

## Full changelog

See [CHANGELOG.md](CHANGELOG.md) for commit-by-commit details.

---

## Sommario (Italiano)

Questa PR propone un set di miglioramenti sviluppati sul fork [IlSommoKadam/ScrcpyForAndroid](https://github.com/IlSommoKadam/ScrcpyForAndroid), focalizzati su affidabilità del mirroring, compatibilità Android 14+, esperienza utente e diagnostica.

### Modifiche principali
- Fix schermo nero (timing surface, CONFIG frame, encoder restart)
- Supporto Android 14+ con fallback encoder e touch mapping scalato
- Risoluzione **Auto** (min tra display locale e remoto)
- Rotazione mirror durante sessione attiva
- LED online/offline, pulsanti ADB reboot/power-off, pulsante Power nel mirror
- Log di sessione condivisibili
- UI migliorata (titolo, impostazioni espandibili, opzioni avanzate)

Vedi [CHANGELOG.md](CHANGELOG.md) per il dettaglio completo.
