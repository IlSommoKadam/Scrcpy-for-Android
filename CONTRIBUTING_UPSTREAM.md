# Contributo al progetto originale

Questo documento descrive il branch `cursor/upstream-contribution-cb6e` preparato per una pull request verso il repository originale.

## Repository

| Ruolo | URL |
|-------|-----|
| **Originale (upstream)** | https://github.com/zwc456baby/ScrcpyForAndroid |
| **Fork** | https://github.com/IlSommoKadam/Scrcpy-for-Android |
| **Branch PR** | `cursor/upstream-contribution-cb6e` |

## Obiettivo della PR

Portare nel progetto originale un set coerente di miglioramenti sviluppati sul fork, focalizzati su:

1. **Affidabilità del mirroring** — fix schermo nero, timing surface, encoder restart
2. **Compatibilità Android 14+** — fallback encoder, touch mapping scalato
3. **Esperienza utente** — risoluzione auto, rotazione mirror, controlli ADB, LED stato
4. **Diagnostica** — log di sessione condivisibili

## Come aprire la PR manualmente

> **Nota:** il repository `IlSommoKadam/Scrcpy-for-Android` non risulta registrato come fork GitHub di `zwc456baby/ScrcpyForAndroid`. Per questo motivo il link di confronto automatico potrebbe non funzionare. Usa la procedura "compare across forks" descritta sotto.

1. Vai su https://github.com/zwc456baby/ScrcpyForAndroid/compare/main
2. Clicca **compare across forks**
3. Imposta:
   - **base repository:** `zwc456baby/ScrcpyForAndroid` → branch `main`
   - **head repository:** `IlSommoKadam/Scrcpy-for-Android` → branch `cursor/upstream-contribution-cb6e`
4. Clicca **Create pull request**
5. Copia titolo e descrizione dal file [`PULL_REQUEST.md`](PULL_REQUEST.md):
   - **Titolo:** `Mirroring reliability, Android 14+ support, and UX improvements`
   - **Corpo:** incolla il contenuto completo di `PULL_REQUEST.md`

### Link diretto (se il fork viene collegato in futuro)

```
https://github.com/zwc456baby/ScrcpyForAndroid/compare/main...IlSommoKadam:Scrcpy-for-Android:cursor/upstream-contribution-cb6e?expand=1
```

## Test consigliati prima del merge

- [ ] Connessione ADB a dispositivo remoto su stessa rete
- [ ] Mirroring con risoluzione Auto e risoluzioni fisse
- [ ] Rotazione dispositivo client durante sessione attiva
- [ ] Pulsanti back/home/menu/power nella barra mirror
- [ ] Riavvio e spegnimento via ADB
- [ ] LED online/offline con IP valido e non valido
- [ ] Condivisione log di sessione
- [ ] Dispositivo remoto Android 14+

## Note per i maintainer

- Le stringhe UI includono traduzioni EN/JA/ZH; alcune etichette italiane sono presenti nel file `strings.xml` di default e potrebbero essere localizzate in inglese prima del merge.
- `versionCode`/`versionName` sono stati incrementati nel fork (1.5.20 / r33); il maintainer può decidere la numerazione finale.
- Nessuna dipendenza esterna aggiunta; le modifiche sono compatibili con la struttura Gradle esistente.
