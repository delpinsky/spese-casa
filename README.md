🏠 Spese Casa Mobile v1.0

Un'applicazione web leggera e moderna per la gestione del budget familiare, ottimizzata per l'uso su smartphone e sincronizzata in tempo reale tramite Google Firebase.
✨ Caratteristiche

    Gestione Budget Giornaliero: Ogni giorno ha un budget dedicato (personalizzabile).

    Calcolo Residuo Dinamico: Visualizzazione istantanea di quanto resta per le spese aggregate e per gli extra.

    Sync in Real-time: I dati vengono salvati automaticamente sul cloud.

    Dark Mode: Supporto per il tema scuro.

    Sicurezza: Accesso protetto tramite email e password.

🚀 Guida alla configurazione (Firebase)

<B>Se vuoi clonare questa app o permettere a qualcun altro di usarla con un proprio database, segui questi passaggi:</B>
1. Creare il progetto

    Vai su Firebase Console.

    Clicca su "Aggiungi progetto" e dai un nome (es. "Spese Casa").

    Una volta creato, clicca sull'icona Web (</>) per registrare l'app.

    Copia l'oggetto firebaseConfig che ti verrà mostrato.

2. Attivare l'Autenticazione

    Nel menu a sinistra, vai su Authentication > Get Started.

    Scegli il metodo Email/Password e abilitalo.

    Vai nella tab Users e clicca su "Add user" per creare le tue credenziali di accesso.

3. Configurare il Database (Firestore)

    Vai su Firestore Database > Create database.

    Scegli la località più vicina a te e avvia in "Test mode" (poi aggiorneremo le regole).

    Clicca sulla tab Rules e incolla queste regole per proteggere i tuoi dati:

JavaScript

service cloud.firestore {
  match /databases/{database}/documents {
    match /spese/spese-famiglia {
      allow read, write: if request.auth != null && request.auth.token.email == "TUA_EMAIL@ESEMPIO.COM";
    }
  }
}

(Sostituisci TUA_EMAIL@ESEMPIO.COM con l'email che userai per loggarti).
4. Collegare l'App

    Apri il file spese_mobile.html con un editor di testo.

    Cerca la costante firebaseConfig.

    Sostituisci i valori con quelli copiati al punto 1.4.

    Salva e carica il file su un hosting (es. GitHub Pages, Netlify o semplicemente usalo localmente).

🛠️ Tecnologie utilizzate

    HTML5 / CSS3 / JS (ES6+)

    Google Firebase (Auth & Firestore)

    Google Fonts (DM Sans & DM Mono)

Versione: 1.0

Autore: Creato con amore (e un pizzico di AI) per una gestione finanziaria senza stress.
