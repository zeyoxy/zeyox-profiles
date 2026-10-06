# Zeyox Profiles — V1

Base de site de profils personnalisés pour `www.zeyoxmc.qd.je`.

## Fonctionnalités
- inscription / connexion
- session HTTP-only
- profil public `/@pseudo`
- nom affiché, bio, avatar, couleurs
- liens personnalisés
- stockage persistant dans Cloudflare D1
- frontend servi par Cloudflare Pages
- `_worker.js` pour l'API et les routes `@pseudo`

## Mise en ligne Cloudflare

### 1. Créer la base D1
Dans Cloudflare : **Storage & databases → D1 → Create database**.

Nom suggéré : `zeyox-profiles-db`

Puis exécute `sql/schema.sql` dans le SQL console de D1.

### 2. Lier D1 au projet Pages
Dans **Workers & Pages → zeyoxmc → Settings → Bindings** :

- Add → D1 database
- Variable name : `DB`
- Database : `zeyox-profiles-db`

Redeploy le projet après avoir ajouté le binding.

### 3. Déployer les fichiers
Le dossier à envoyer est la racine du projet (`public/*` + `_worker.js`).

Le mode Direct Upload de Pages prend en charge `_worker.js` ; le dossier `functions/` n'est pas nécessaire ici.

## Important
La V1 est une base fonctionnelle. Avant une ouverture publique, ajoute de la vérification d'email, un système de reset de mot de passe, du rate limiting et une vraie politique anti-abus.
