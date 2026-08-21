# Changelog

All significant changes in the fork [IlSommoKadam/ScrcpyForAndroid](https://github.com/IlSommoKadam/ScrcpyForAndroid) compared to the upstream project [zwc456baby/ScrcpyForAndroid](https://github.com/zwc456baby/ScrcpyForAndroid).

**Current version:** 1.5.20 (r33)

---

Tutte le modifiche significative apportate al fork [IlSommoKadam/ScrcpyForAndroid](https://github.com/IlSommoKadam/ScrcpyForAndroid) rispetto al progetto originale [zwc456baby/ScrcpyForAndroid](https://github.com/zwc456baby/ScrcpyForAndroid).

**Versione attuale:** 1.5.20 (r33)

---

## [1.5.20] — r33

### Added / Aggiunto
- **Power off Android (ADB)** button below the reboot button on the main screen
- Confirmation dialog before sending `adb shell reboot -p`

- Pulsante **Spegni Android (ADB)** sotto il pulsante di riavvio nella schermata principale
- Dialog di conferma prima dell'invio del comando `adb shell reboot -p`

## [1.5.19] — r32

### Added / Aggiunto
- **Power** button in the mirror navigation bar (next to back/home/menu)
- Sends `KEYCODE_POWER` to the remote device during mirroring

- Pulsante **Power** nella barra di navigazione del mirror (accanto a back/home/menu)
- Invio comando `KEYCODE_POWER` al dispositivo remoto durante la sessione di mirroring

## [1.5.18] — r31

### Added / Aggiunto
- **Reboot Android (ADB)** button on the main screen
- **Online/offline** status LED next to the IP field (green = reachable, red = offline)
- Periodic ADB connectivity check to the remote device

- Pulsante **Riavvia Android (ADB)** nella schermata principale
- LED di stato **online/offline** accanto al campo IP (verde = raggiungibile, rosso = offline)
- Verifica periodica della connettività ADB al dispositivo remoto

## [1.5.17] — r30

### Fixed / Corretto
- Black screen caused by skipped CONFIG frames after surface rotation
- Encoder restart lag: encoder stays alive after producing the first frame
- SPS/PPS parsing always runs even after surface rotation
- Skip unnecessary v4l2 path on Android

- Schermo nero causato da CONFIG frame saltati dopo rotazione del surface
- Lag al riavvio dell'encoder: l'encoder resta attivo dopo il primo frame
- Parsing SPS/PPS sempre eseguito anche dopo rotazione del surface
- Skip del path v4l2 non necessario su Android

## [1.5.16] — r29

### Fixed / Corretto
- `AutoResolution` constructor visibility for `MainActivity`

- Visibilità del costruttore `AutoResolution` per `MainActivity`

## [1.5.12] — r28

### Added / Improved — Aggiunto / Migliorato
- **Android 14+** mirroring support with encoder fallback
- **Scaled touch mapping** for different client/server resolutions
- Automatic fallback between hardware encoders when the primary fails
- **Session log** system (`SessionLog`) shareable via email/WhatsApp
- `LogFileProvider` for secure log sharing
- Advanced options: video codec, max FPS, custom encoder
- Expandable/collapsible settings panel

- Supporto mirroring su **Android 14+** con fallback encoder
- **Touch mapping scalato** per risoluzioni diverse tra client e server
- Fallback automatico tra encoder hardware
- Sistema di **log di sessione** (`SessionLog`) condivisibile via email/WhatsApp
- `LogFileProvider` per condivisione sicura dei log
- Opzioni avanzate: codec video, FPS massimi, encoder personalizzato
- Pannello impostazioni espandibile/collassabile

### Fixed / Corretto
- More reliable `ExecUtil` for ADB commands
- Structured ADB operations via `AdbHelper`

- Gestione `ExecUtil` per comandi ADB più affidabili
- `AdbHelper` per operazioni ADB strutturate

## [1.5.11] — r27

### Added / Aggiunto
- **Auto** resolution mode: computes the minimum between local and remote display
- `ResolutionHelper` queries local display and remote `wm size` via ADB
- Resolution preview in UI with limit indication (local or remote)
- Localized strings EN/JA/ZH for Auto mode

- Modalità risoluzione **Auto**: calcola il minimo tra display locale e remoto
- `ResolutionHelper` interroga il display locale e `wm size` remoto via ADB
- Anteprima risoluzione in UI con indicazione del limite (locale o remoto)
- Stringhe localizzate EN/JA/ZH per la modalità Auto

## [1.5.10] — r26

### Added / Aggiunto
- **Mirror rotation** during active scrcpy session (`FULL_SENSOR`)
- Mirror layout reinflate for portrait/landscape with `layout-land` resources
- Video surface rebind on rotation without restarting the scrcpy service
- Remote rotation handler on main thread, connection kept alive

- **Rotazione del mirror** durante la sessione scrcpy (`FULL_SENSOR`)
- Reinflate del layout mirror per portrait/landscape con risorse `layout-land`
- Rebind della surface video alla rotazione senza riavviare il servizio
- Handler rotazione remota sul main thread, connessione mantenuta

### Fixed / Corretto
- `onStop` does not disconnect when the activity is rotating (`isChangingConfigurations`)

- `onStop` non disconnette quando l'activity sta ruotando (`isChangingConfigurations`)

## [1.5.9] — r25

### Fixed / Corretto
- Black screen from incorrect surface timing: wait for `SurfaceHolder` callback before starting the service
- Surface re-bind on resume and surface changes to avoid stale/invalid surfaces
- Surface validation before video decoder configuration
- Decoder error logging

- Schermo nero per timing errato della surface: attesa del callback `SurfaceHolder`
- Re-bind della surface su resume e cambi surface
- Validazione surface prima della configurazione del video decoder
- Log degli errori del decoder

### Improved / Migliorato
- Styled app title with subtitle
- Fixed typo "Hight" → "High" in delay control
- Removed debug log tag

- Titolo app con nome stilizzato e sottotitolo
- Corretto typo "Hight" → "High" nel delay control
- Rimosso tag di debug dal log

---

## Modified files summary / Riepilogo file modificati

**38 files · +2534 / −381 lines**

| Area | Main files / File principali |
|------|------------------------------|
| **Client UI** | `MainActivity.java`, `activity_main.xml`, `surface.xml`, `strings.xml` |
| **Client core** | `Scrcpy.java`, `Options.java`, `VideoDecoder.java`, `SendCommands.java` |
| **Client utils** | `ResolutionHelper.java`, `SessionLog.java`, `AdbHelper.java`, `ExecUtil.java` |
| **Server** | `ScreenEncoder.java`, `ScreenCapture.java`, `Device.java`, `Options.java` |
| **Server wrappers** | `DisplayManager.java`, `InputManager.java`, `SurfaceControl.java` |

---

## Authors / Autori

- [IlSommoKadam](https://github.com/IlSommoKadam)
- Contributions assisted by Cursor Agent / Contributi assistiti da Cursor Agent
