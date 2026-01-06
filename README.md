# Whisper

Une app macOS ultra simple pour transcrire ta voix en texte, directement depuis ta barre de menu.

Maintiens la touche **Fn** enfoncée, parle, relâche, et le texte apparaît là où se trouve ton curseur. C'est tout.

## Comment ça marche ?

1. L'app vit dans ta barre de menu (en haut à droite de ton écran)
2. Tu maintiens la touche **Fn** enfoncée
3. Tu parles
4. Tu relâches **Fn**
5. Le texte transcrit est automatiquement collé là où tu étais en train d'écrire

L'app utilise l'API OpenAI Whisper pour la transcription. C'est rapide, précis, et ça comprend super bien le français (y compris le vocabulaire tech : API, SDK, React, Node.js, etc.).

## Installation

### Prérequis

- macOS 14 (Sonoma) ou plus récent
- Une clé API OpenAI ([créer un compte ici](https://platform.openai.com/api-keys))
- Xcode (pour compiler l'app)

### Étapes

1. **Clone le repo**
   ```bash
   git clone https://github.com/Paseru/whisper.git
   cd whisper
   ```

2. **Ouvre le projet dans Xcode**
   ```bash
   open Whisper.xcodeproj
   ```

3. **Compile et lance** (Cmd + R)

4. **Configure ta clé API**
   - Clique sur l'icône Whisper dans la barre de menu
   - Va dans les réglages
   - Entre ta clé API OpenAI (commence par `sk-...`)

5. **Accorde les permissions**
   - **Microphone** : pour enregistrer ta voix
   - **Accessibilité** : pour coller le texte automatiquement

## Lancer Whisper au démarrage du Mac

Pour que Whisper se lance automatiquement quand tu allumes ton Mac :

1. Ouvre **Réglages Système**
2. Va dans **Général** > **Ouverture**
3. Clique sur le **+** en bas de la liste
4. Cherche et sélectionne **Whisper** dans tes Applications
5. C'est bon !

Maintenant Whisper sera toujours prêt à t'écouter dès que tu démarres ton Mac.

## Fonctionnalités

### Transcription instantanée
Maintiens **Fn**, parle, relâche. Le texte apparaît. Simple.

### Historique (24h)
L'app garde un historique de tes transcriptions des dernières **24 heures**. Pratique pour retrouver un truc que t'as dicté plus tôt.

- Clique sur l'icône dans la barre de menu
- Sélectionne "Historique"
- Clique sur une transcription pour la copier

L'historique se nettoie automatiquement après 24h pour ne pas encombrer ton Mac.

### Feedback audio
Un petit son te confirme quand l'enregistrement commence et quand la transcription est prête.

## Permissions requises

L'app a besoin de ces permissions pour fonctionner :

| Permission | Pourquoi ? |
|------------|-----------|
| **Microphone** | Pour enregistrer ta voix |
| **Accessibilité** | Pour coller le texte automatiquement dans n'importe quelle app |

## Clé API OpenAI

Tu as besoin d'une clé API OpenAI pour utiliser Whisper :

1. Va sur [platform.openai.com/api-keys](https://platform.openai.com/api-keys)
2. Crée un compte ou connecte-toi
3. Crée une nouvelle clé API
4. Copie la clé (elle commence par `sk-...`)
5. Colle-la dans les réglages de Whisper

**Note** : L'utilisation de l'API est payante, mais la transcription audio coûte très peu (~0.006$/minute). Consulte les [tarifs OpenAI](https://openai.com/pricing) pour plus de détails.

Ta clé API est stockée de façon sécurisée dans le Keychain de macOS (le même endroit où sont stockés tes mots de passe).

## Comment ça fonctionne techniquement ?

1. Quand tu appuies sur **Fn**, l'app commence à enregistrer ton micro
2. L'audio est enregistré en format M4A (16kHz, mono)
3. Quand tu relâches **Fn**, l'audio est envoyé à l'API OpenAI Whisper
4. Le texte transcrit revient en quelques secondes
5. L'app simule un Cmd+V pour coller le texte là où tu étais

## Confidentialité

- **Audio** : Envoyé à OpenAI pour transcription, puis supprimé localement
- **Clé API** : Stockée dans le Keychain macOS (chiffré)
- **Historique** : Stocké localement, supprimé après 24h
- **Aucune télémétrie** : L'app n'envoie aucune donnée ailleurs qu'à OpenAI pour la transcription

## Contribuer

Les PRs sont les bienvenues ! Si tu trouves un bug ou tu as une idée de feature, ouvre une issue.

## Licence

MIT - Fais-en ce que tu veux !
