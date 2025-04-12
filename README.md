# 🤖 Assistant IA Mobile – Flutter + Firebase Studio + OpenAI

Bienvenue dans ce projet de démonstration d'une application mobile Flutter connectée à Firebase Studio et à l'API ChatGPT (OpenAI).

🎯 **Objectif :**  
Explorer et tester les capacités de **Firebase Studio** pour créer une application mobile Flutter intégrant une intelligence artificielle (ChatGPT), sans expertise mobile avancée.

---

## 🧠 Fonctionnalités

- Interface avec deux onglets :
  - **Assistant IA** : Posez une question, recevez la réponse de ChatGPT.
  - **Tutoriel** : Accédez à toutes les étapes du projet, avec des liens utiles.
- Appels sécurisés à l’API OpenAI via **Firebase Cloud Functions**
- Interface Flutter responsive (Android, iOS, Web)

---

## 🧱 Stack Technique

| Composant        | Description                                  |
|------------------|----------------------------------------------|
| **Flutter**      | UI mobile multiplateforme                    |
| **Firebase Studio** | Backend visuel + Cloud Functions            |
| **OpenAI API**   | Fournit les réponses de l'assistant IA       |

---

## ⚙️ Configuration locale

### 1. Prérequis

- [Flutter installé](https://flutter.dev/docs/get-started/install)
- [Firebase CLI](https://firebase.google.com/docs/cli)
- Un compte Firebase
- Une clé API OpenAI

### 2. Cloner le dépôt

```bash
git clone https://github.com/TON_UTILISATEUR/flutter-gpt-assistant.git
cd flutter-gpt-assistant
flutter pub get
```

### 3. Lancer l'application

Lance un émulateur ou connecte un appareil physique :

```bash
flutter run
```

---

## 🔥 Déploiement Firebase

### 1. Initialiser Firebase Functions

```bash
firebase login
firebase init functions
cd functions
npm install axios
```

### 2. Créer la Cloud Function `chatWithGPT`

```js
const functions = require("firebase-functions");
const axios = require("axios");

exports.chatWithGPT = functions.https.onRequest(async (req, res) => {
  const prompt = req.body.prompt;
  try {
    const response = await axios.post("https://api.openai.com/v1/chat/completions", {
      model: "gpt-3.5-turbo",
      messages: [{ role: "user", content: prompt }],
    }, {
      headers: {
        "Authorization": `Bearer YOUR_OPENAI_API_KEY`,
        "Content-Type": "application/json"
      }
    });
    res.send({ reply: response.data.choices[0].message.content });
  } catch (error) {
    res.status(500).send("Erreur API GPT");
  }
});
```

> Remplace `YOUR_OPENAI_API_KEY` par ta clé OpenAI

### 3. Déployer la fonction

```bash
firebase deploy --only functions
```

---

## 🧪 Tests

- Lancement via `flutter run`
- Appel à la fonction Firebase
- Réponses correctes de l’IA dans l’UI

---

## 📘 Tutoriel intégré dans l’app

Un onglet `📘 Tutoriel` te donne :
- 📚 Les étapes du projet
- 🔗 Liens vers la doc officielle
- 📺 Vidéos YouTube utiles

---

## ✨ Prompt utilisé dans Firebase Studio

```plaintext
Tu es un assistant expert en développement mobile Flutter et Firebase. Je veux que tu m’aides à générer une application mobile Flutter simple, multiplateforme (Android, iOS, Web), qui utilise Firebase comme backend et l’API ChatGPT comme moteur IA.

🎯 Objectif :
- Interface utilisateur simple avec un champ texte et un bouton “Envoyer”
- Réponse IA affichée en dessous
- Onglet tutoriel intégré
- Appel sécurisé à l’API ChatGPT via Firebase Cloud Functions
```

---

## 📚 Ressources utiles

- [Flutter – Installer](https://flutter.dev/docs/get-started/install)
- [Firebase Studio](https://firebase.google.com/products/extensions)
- [Cloud Functions – Guide](https://firebase.google.com/docs/functions)
- [API ChatGPT (OpenAI)](https://platform.openai.com/docs/api-reference/chat)
- [Cours Flutter – YouTube](https://www.youtube.com/watch?v=x0uinJvhNxI)

---

## 🪪 Licence

Ce projet est sous licence MIT – voir le fichier `LICENSE` pour plus d’informations.

---

## 🧑‍💻 Auteur

Créé par **@Vlad_K** – N’hésite pas à forker, cloner ou améliorer ce projet 🙌  

---
