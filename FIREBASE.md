# Base de données des inscriptions (Firebase Firestore)

Le site enregistre chaque inscription dans Firestore. La page `admin.html` (espace enseignant, connexion Google) permet de les consulter, filtrer, marquer « fiche signée reçue », choisir un statut et exporter en CSV.

## Mise en place (10 minutes, gratuit)
1. https://console.firebase.google.com > Ajouter un projet (ex. `club-cyber-oued-ellil`). Google Analytics : non.
2. Créer une base : **Build > Firestore Database > Créer une base de données**, mode production, région `eur3` (Europe).
3. Onglet **Règles** : coller le contenu de `firestore.rules` en remplaçant `VOTRE_ADRESSE@gmail.com` par ton adresse Gmail, puis Publier.
4. **Build > Authentication > Commencer > Google > Activer** (choisir ton e-mail d'assistance).
   Puis **Settings > Authorized domains > Add domain** : `mo7amedzouaghi.github.io`.
5. **Paramètres du projet (roue dentée) > Vos applications > icône Web `</>`** : enregistrer l'application, copier l'objet `firebaseConfig`.
6. Dans `firebase-config.js`, remplacer `window.FIREBASE_CONFIG = null;` par `window.FIREBASE_CONFIG = { ... };` avec cet objet.

## Utilisation
- Les élèves s'inscrivent sur `/index.html` : l'inscription est enregistrée, la fiche signée reste à remettre.
- Toi : `/admin.html` > Se connecter avec Google (compte autorisé dans les règles).

## Sécurité
- La configuration Firebase est publique par conception ; ce sont les **règles** qui protègent les données : n'importe qui peut créer une inscription valide, seul ton compte Gmail peut lire, modifier ou supprimer.
- Ne partage pas l'adresse `admin.html` inutilement (elle est de toute façon protégée par la connexion).
- Les données concernent des mineurs : exporte-les seulement si nécessaire et supprime-les en fin d'année.
