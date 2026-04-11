# 🏠 Spese Casa

App per la gestione delle spese mensili familiari, disponibile in versione **desktop** e **mobile PWA**.

---

## 📱 File

| File | Descrizione |
|------|-------------|
| `spese_mensili_casa_v2.html` | Versione desktop (PC) |
| `spese_mobile.html` | Versione mobile (PWA installabile) |
| `manifest.json` | Manifest PWA per installazione su smartphone |

---

## 🚀 Installazione mobile (PWA)

1. Pubblica i file su GitHub Pages
2. Apri l'URL in **Safari** (iOS) o **Chrome** (Android)
3. Tocca **Condividi → Aggiungi alla schermata Home**
4. L'app si apre a schermo intero come un'app nativa

---

## ☁️ Sincronizzazione

I dati vengono sincronizzati in tempo reale tramite **Firebase Firestore** tra desktop e mobile. In caso di assenza di connessione, i dati vengono salvati in locale e sincronizzati al ripristino della connessione.

È sempre possibile esportare e importare i dati manualmente in formato **JSON**.

---

## 📋 Struttura budget mensile

| Giorno | Budget |
|--------|--------|
| Domenica | 0 € |
| Lunedì | 30 € |
| Sabato | 50 € |
| Altri giorni | 40 € |

Budget mensile totale: **1.200 €** (spesa + extra)

---

## 📄 Changelog

---

### v1.1 — Aprile 2026

#### Desktop (`spese_mensili_casa_v2.html`)
- **Nuovo:** pulsante `+` invisibile nelle celle Supermercato, Panificio, Tigotà, Farmacia, Bollette, Extra — appare al passaggio del mouse sulla riga
- **Nuovo:** click sul `+` apre un popover inline per aggiungere un importo a quello esistente nella cella
- **Nuovo:** il popover si chiude automaticamente dopo l'aggiunta o cliccando fuori
- **Fix:** pulsanti Esporta/Carica non duplicati nell'header

#### Mobile (`spese_mobile.html`)
- **Nuovo:** pulsante `+` visibile a destra di ogni campo importo (Supermercato, Panificio, Tigotà, Farmacia, Bollette, Extra) quando la card del giorno è aperta
- **Nuovo:** tap sul `+` apre un popover con campo numerico per aggiungere un importo
- **Nuovo:** il `+` è allineato al bordo destro della card, in linea con il saldo mostrato nell'header della card
- **Miglioramento:** campo input si allunga fino al pulsante `+` per un layout più ordinato

---

### v1.0 — Aprile 2026

#### Desktop (`spese_mensili_casa_v2.html`)
- **Nuovo:** app per la gestione delle spese mensili su browser desktop
- **Nuovo:** tabella con colonne Giorno, Budget, Supermercato, Resto, Panificio, Tigotà, Farmacia, Bollette, Extra
- **Nuovo:** budget giornaliero differenziato per giorno della settimana (Dom 0 €, Lun 30 €, Sab 50 €, altri 40 €)
- **Nuovo:** colonna Resto con saldo giornaliero in verde (+) o rosso (−)
- **Nuovo:** barra di riepilogo con totali: Spese Supermercato, Spese Aggregato, Saldo, Farmacia+Boll+Extra
- **Nuovo:** totali in fondo tabella con Budget spesa, Budget extra, Totale generale
- **Nuovo:** navigazione tra mesi con frecce ◀ ▶
- **Nuovo:** modalità chiara/scura
- **Nuovo:** pannello Impostazioni con colore header, font, dimensione testo globale, dimensione e colore cifre nelle celle
- **Nuovo:** sincronizzazione Firebase Firestore in tempo reale
- **Nuovo:** salvataggio automatico 1,5 secondi dopo l'ultima modifica
- **Nuovo:** barra stato sincronizzazione (Sincronizzato / Salvataggio / Offline / Errore)
- **Nuovo:** export/import dati in formato JSON
- **Nuovo:** autenticazione con email e password tramite Firebase Auth
- **Nuovo:** numero versione `v1.0` nell'header

#### Mobile (`spese_mobile.html`)
- **Nuovo:** PWA installabile su iOS e Android
- **Nuovo:** layout a card per giorno, touch-friendly
- **Nuovo:** card del giorno corrente aperta automaticamente all'avvio e in evidenza (bordo blu)
- **Nuovo:** barra di progresso spesa vs budget in ogni card
- **Nuovo:** saldo giornaliero in verde/rosso nell'header della card
- **Nuovo:** navigazione tra mesi
- **Nuovo:** modalità chiara/scura
- **Nuovo:** sincronizzazione Firebase Firestore condivisa con la versione desktop
- **Nuovo:** salvataggio automatico con indicatore di stato
- **Nuovo:** export/import dati JSON
- **Nuovo:** autenticazione con email e password
- **Nuovo:** footer fisso con totali aggregati e residuo budget
- **Nuovo:** numero versione `v1.1` nell'header

---

## 🔐 Sicurezza Firebase

Le regole Firestore limitano l'accesso fino al **31 dicembre 2027**. Prima di tale data aggiornare le regole nella console Firebase:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /spese/{document=**} {
      allow read, write: if request.time < timestamp.date(2027, 12, 31);
    }
  }
}
```

---

## 🛠️ Tecnologie utilizzate

- HTML5 / CSS3 / JavaScript (ES Modules)
- [Firebase Firestore](https://firebase.google.com/) — database cloud in tempo reale
- [Firebase Authentication](https://firebase.google.com/) — autenticazione utenti
- PWA (Progressive Web App) con `manifest.json`
- Google Fonts: DM Sans, DM Mono
