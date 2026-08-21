# Contributing to the upstream project / Contributo al progetto originale

This document describes the branch `cursor/branch-setup-bf00`, which includes all fork improvements and contribution docs for a pull request to the original repository.

Questo documento descrive il branch `cursor/branch-setup-bf00`, che include tutti i miglioramenti del fork e la documentazione di contributo per una pull request verso il repository originale.

## Repositories / Repository

| Role / Ruolo | URL |
|--------------|-----|
| **Upstream (original)** | https://github.com/zwc456baby/ScrcpyForAndroid |
| **Official fork** | https://github.com/IlSommoKadam/ScrcpyForAndroid |
| **PR branch** | `cursor/branch-setup-bf00` |

## PR goal / Obiettivo della PR

Bring a coherent set of improvements to the upstream project:

1. **Mirroring reliability** — black screen fixes, surface timing, encoder restart
2. **Android 14+ compatibility** — encoder fallback, scaled touch mapping
3. **User experience** — auto resolution, mirror rotation, ADB controls, status LED
4. **Diagnostics** — shareable session logs

Portare nel progetto originale un set coerente di miglioramenti:

1. **Affidabilità del mirroring** — fix schermo nero, timing surface, encoder restart
2. **Compatibilità Android 14+** — fallback encoder, touch mapping scalato
3. **Esperienza utente** — risoluzione auto, rotazione mirror, controlli ADB, LED stato
4. **Diagnostica** — log di sessione condivisibili

## Push branch to the official fork / Push del branch sul fork ufficiale

> **Important:** The branch was initially pushed to `IlSommoKadam/Scrcpy-for-Android` (a separate repo). It must be pushed to the **official fork** `IlSommoKadam/ScrcpyForAndroid` before opening the upstream PR.
>
> **Importante:** Il branch è stato inizialmente pushato su `IlSommoKadam/Scrcpy-for-Android` (repo separato). Deve essere pushato sul **fork ufficiale** `IlSommoKadam/ScrcpyForAndroid` prima di aprire la PR verso upstream.

```bash
# Add the official fork as remote / Aggiungi il fork ufficiale come remote
git remote add official https://github.com/IlSommoKadam/ScrcpyForAndroid.git

# Push the contribution branch / Pusha il branch di contributo
git push -u official cursor/branch-setup-bf00

# Optionally push main with all improvements / Opzionale: pusha main con tutti i miglioramenti
git push official main
```

## How to open the upstream PR / Come aprire la PR verso upstream

Since `IlSommoKadam/ScrcpyForAndroid` is a registered GitHub fork of upstream, the compare link works directly:

Poiché `IlSommoKadam/ScrcpyForAndroid` è un fork GitHub registrato di upstream, il link di confronto funziona direttamente:

1. Open / Apri: https://github.com/zwc456baby/ScrcpyForAndroid/compare/main...IlSommoKadam:ScrcpyForAndroid:cursor/branch-setup-bf00?expand=1
2. Click **Create pull request** / Clicca **Create pull request**
3. Use title and body from [`PULL_REQUEST.md`](PULL_REQUEST.md):
   - **Title / Titolo:** `Mirroring reliability, Android 14+ support, and UX improvements`
   - **Body / Corpo:** paste the full content of `PULL_REQUEST.md`

## Recommended tests before merge / Test consigliati prima del merge

- [ ] ADB connection to remote device on same network / Connessione ADB su stessa rete
- [ ] Mirroring with Auto and fixed resolutions / Mirroring con risoluzione Auto e fisse
- [ ] Client device rotation during active session / Rotazione dispositivo client durante sessione
- [ ] Mirror bar buttons: back, home, menu, power / Pulsanti back/home/menu/power
- [ ] ADB reboot and power-off / Riavvio e spegnimento via ADB
- [ ] Online/offline LED with valid and invalid IP / LED stato con IP valido e non valido
- [ ] Session log sharing / Condivisione log di sessione
- [ ] Remote device on Android 14+ / Dispositivo remoto Android 14+

## Notes for maintainers / Note per i maintainer

- UI strings include EN/JA/ZH translations; some Italian labels are in the default `strings.xml` and can be localized to English before merge.
- `versionCode`/`versionName` were incremented in the fork (1.5.20 / r33); the maintainer can decide the final numbering.
- No external dependencies added; changes are compatible with the existing Gradle structure.

- Le stringhe UI includono traduzioni EN/JA/ZH; alcune etichette italiane sono nel `strings.xml` di default.
- `versionCode`/`versionName` incrementati nel fork (1.5.20 / r33).
- Nessuna dipendenza esterna aggiunta.
