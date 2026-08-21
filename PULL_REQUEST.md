# Pull Request — Miglioramenti mirroring, Android 14+ e UX

## Sommario

Questa PR propone un set di miglioramenti sviluppati sul fork [IlSommoKadam/Scrcpy-for-Android](https://github.com/IlSommoKadam/Scrcpy-for-Android), focalizzati su affidabilità del mirroring, compatibilità Android 14+, esperienza utente e diagnostica.

**10 commit** · **38 file** · **+2534 / −391 righe**

## Modifiche principali

### Fix affidabilità mirroring
- Risolto schermo nero causato da timing errato della `Surface` (attesa callback `SurfaceHolder` prima di avviare il servizio)
- Re-bind automatico della surface su resume e cambi configurazione
- Fix CONFIG frame saltati dopo rotazione: parsing SPS/PPS sempre attivo
- Encoder non riavviato inutilmente dopo il primo frame prodotto (elimina lag)

### Android 14+ e encoder
- Fallback automatico tra encoder hardware quando il primario fallisce
- Touch mapping scalato per risoluzioni diverse tra client e server
- Miglioramenti a `ScreenEncoder`, `ScreenCapture` e wrapper di sistema

### Risoluzione automatica
- Nuova modalità **Auto**: calcola il minimo tra display locale e remoto via ADB (`wm size`)
- `ResolutionHelper` con anteprima in UI e indicazione del limite attivo
- Stringhe localizzate EN/JA/ZH

### Rotazione durante sessione
- Mirror ruotabile con `FULL_SENSOR` senza disconnessione
- Reinflate layout portrait/landscape con risorse `layout-land`
- Rebind surface video alla rotazione senza restart del servizio scrcpy

### Controlli e stato dispositivo
- LED online/offline accanto al campo IP (verifica connettività ADB)
- Pulsante riavvio ADB (`adb reboot`) con dialog di conferma
- Pulsante spegnimento ADB (`adb reboot -p`) con dialog di conferma
- Pulsante Power nella barra di navigazione del mirror

### Diagnostica
- `SessionLog`: log di sessione resettato ad ogni avvio, condivisibile via email/WhatsApp
- `LogFileProvider` per condivisione sicura dei file di log

### UI
- Titolo app stilizzato con sottotitolo
- Pannello impostazioni espandibile/collassabile
- Opzioni avanzate: codec video, FPS max, encoder personalizzato

## File toccati

<details>
<summary>Elenco completo (38 file)</summary>

**Client:** `MainActivity.java`, `Scrcpy.java`, `Options.java`, `VideoDecoder.java`, `ResolutionHelper.java`, `SessionLog.java`, `AdbHelper.java`, `ExecUtil.java`, layout XML, strings EN/JA/ZH

**Server:** `ScreenEncoder.java`, `ScreenCapture.java`, `Device.java`, `Options.java`, `DisplayManager.java`, `InputManager.java`, `SurfaceControl.java`

</details>

## Test effettuati

- Mirroring su rete locale con risoluzione Auto e fissa
- Rotazione dispositivo client durante sessione attiva
- Pulsanti navigazione mirror (back, home, menu, power)
- Comandi ADB reboot e power off
- LED stato con IP valido/non valido

## Note

- Alcune stringhe UI nel `strings.xml` di default sono in italiano; possono essere convertite in inglese se preferito.
- `versionCode`/`versionName` incrementati nel fork (1.5.20 / r33); numerazione a discrezione del maintainer.
- Nessuna nuova dipendenza esterna.

## Changelog completo

Vedi [CHANGELOG.md](CHANGELOG.md) per il dettaglio commit per commit.
