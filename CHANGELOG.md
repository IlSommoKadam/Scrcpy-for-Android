# Changelog

Tutte le modifiche significative apportate al fork [IlSommoKadam/Scrcpy-for-Android](https://github.com/IlSommoKadam/Scrcpy-for-Android) rispetto al progetto originale [zwc456baby/ScrcpyForAndroid](https://github.com/zwc456baby/ScrcpyForAndroid).

**Versione attuale:** 1.5.20 (r33)

---

## [1.5.20] — r33

### Aggiunto
- Pulsante **Spegni Android (ADB)** sotto il pulsante di riavvio nella schermata principale
- Conferma dialog prima dell'invio del comando `adb shell reboot -p`

## [1.5.19] — r32

### Aggiunto
- Pulsante **Power** nella barra di navigazione del mirror (accanto a back/home/menu)
- Invio comando `KEYCODE_POWER` al dispositivo remoto durante la sessione di mirroring

## [1.5.18] — r31

### Aggiunto
- Pulsante **Riavvia Android (ADB)** nella schermata principale
- LED di stato **online/offline** accanto al campo IP (verde = dispositivo raggiungibile, rosso = offline)
- Verifica periodica della connettività ADB al dispositivo remoto

## [1.5.17] — r30

### Corretto
- Schermo nero causato da CONFIG frame saltati dopo rotazione del surface
- Lag al riavvio dell'encoder: l'encoder resta attivo dopo aver prodotto il primo frame
- Parsing SPS/PPS sempre eseguito anche dopo rotazione del surface
- Skip del path v4l2 non necessario su Android

## [1.5.16] — r29

### Corretto
- Visibilità del costruttore `AutoResolution` per `MainActivity`

## [1.5.12] — r28

### Aggiunto / Migliorato
- Supporto mirroring su **Android 14+** con fallback encoder
- **Touch mapping scalato** per risoluzioni diverse tra client e server
- Fallback automatico tra encoder hardware quando il primario fallisce
- Sistema di **log di sessione** (`SessionLog`) con condivisione via email/WhatsApp
- `LogFileProvider` per condivisione sicura dei log
- Opzioni avanzate: codec video, FPS massimi, encoder personalizzato
- Pannello impostazioni espandibile/collassabile

### Corretto
- Gestione `ExecUtil` per comandi ADB più affidabili
- `AdbHelper` per operazioni ADB strutturate

## [1.5.11] — r27

### Aggiunto
- Modalità risoluzione **Auto**: calcola il minimo tra display locale e remoto
- `ResolutionHelper` interroga il display locale e `wm size` remoto via ADB
- Anteprima risoluzione in UI con indicazione del limite (locale o remoto)
- Stringhe localizzate EN/JA/ZH per la modalità Auto

## [1.5.10] — r26

### Aggiunto
- **Rotazione del mirror** durante la sessione scrcpy (`FULL_SENSOR`)
- Reinflate del layout mirror per portrait/landscape con risorse `layout-land`
- Rebind della surface video alla rotazione senza riavviare il servizio
- Handler rotazione remota sul main thread, connessione mantenuta

### Corretto
- `onStop` non disconnette quando l'activity sta ruotando (`isChangingConfigurations`)

## [1.5.9] — r25

### Corretto
- Schermo nero per timing errato della surface: attesa del callback `SurfaceHolder` prima di avviare il servizio
- Re-bind della surface su resume e cambi surface per evitare surface stale/invalide
- Validazione surface prima della configurazione del video decoder
- Log degli errori del decoder

### Migliorato
- Titolo app con nome stilizzato e sottotitolo
- Corretto typo "Hight" → "High" nel delay control
- Rimosso tag di debug dal log

---

## Riepilogo file modificati (38 file, +2534 / −391 righe)

| Area | File principali |
|------|-----------------|
| **Client UI** | `MainActivity.java`, `activity_main.xml`, `surface.xml`, `strings.xml` |
| **Client core** | `Scrcpy.java`, `Options.java`, `VideoDecoder.java`, `SendCommands.java` |
| **Client utils** | `ResolutionHelper.java`, `SessionLog.java`, `AdbHelper.java`, `ExecUtil.java` |
| **Server** | `ScreenEncoder.java`, `ScreenCapture.java`, `Device.java`, `Options.java` |
| **Server wrappers** | `DisplayManager.java`, `InputManager.java`, `SurfaceControl.java` |

---

## Autori

- [IlSommoKadam](https://github.com/IlSommoKadam)
- Contributi assistiti da Cursor Agent
