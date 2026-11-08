# Mon Budget — V2.0.0 · Cahier de comptes

Application personnelle, indépendante, en français. Une nouvelle interface orientée **tableaux mensuels, colonnes Prévu/Réel et bilan annuel**, en s'inspirant du principe de suivi budgétaire sous Excel/Google Sheets. **Ce n'est pas FocusDaily et aucun fichier, design propriétaire ou template FocusDaily payant n'est inclus**.

## Changement majeur

- Tableau de bord avec revenus, dépenses courantes, frais fixes, crédits/dettes, épargne, indicateurs et graphiques.
- 12 mois par année + récapitulatif annuel sur 12 mois.
- Lignes de tableaux modifiables, boutons de confirmation de paiement.
- Liste complète des transactions : recherche, filtre, modification, copie, report.
- Catégories personnalisables et enveloppes mensuelles optionnelles.
- Coffres d'épargne : objectifs, versements et retraits.
- Une action pour reprendre **seulement** les frais fixes et crédits du mois précédent. Les sorties, anniversaires et randonnées restent ponctuels.
- Dans Paramètres, **uniquement** : « Rechercher les mises à jour », « Exporter une sauvegarde », « Importer une sauvegarde ».
- Toujours utilisable hors ligne après installation du cache ; hébergement GitHub Pages gratuit.

## Mise à jour de V1.x vers V2.0.0

1. **Avant la mise à jour, dans l'application actuelle**, ouvrir les paramètres et utiliser « Exporter une sauvegarde ». Conserver ce fichier JSON dans un dossier privé.
2. Sur l'ordinateur Windows, ouvrir le ZIP et **extraire tous les fichiers**.
3. Ouvrir le dépôt GitHub `Loan-s-Budget` (branche `main`).
4. `Add file` → `Upload files`. Glisser les fichiers extraits, **pas le ZIP**. Remplacer les versions existantes et faire `Commit changes`.
5. Vérifier le déploiement `github-pages` terminé (coche verte dans GitHub).
6. Sur le Samsung, ouvrir l'adresse du site dans **Chrome**, puis aller dans les paramètres de Mon Budget et toucher **« Rechercher les mises à jour »**. Si « Installer la mise à jour » s'affiche, toucher ce bouton. Si Chrome utilise encore une ancienne version, fermer puis rouvrir le site ; sur PC, `Ctrl + Maj + R` peut aider.
7. Vérifier les données. **Ne pas désinstaller l'ancienne application et ne pas effacer les données du navigateur.**

Les anciennes données de la V1.0.0 à V1.2.0 utilisent toujours **IndexedDB `mon-budget-db` version 1**. La V2.0.0 n'efface pas cette base ; elle utilise les mêmes stores et le même format JSON `app: mon-budget`, `format: 1`. Le `manifest.webmanifest` conserve `id: './'` et `start_url: './'` pour maintenir l'identité de la PWA sur le même dépôt.

## Importer les dépenses de novembre

Si Mon Budget est vide, ouvrir Paramètres → Importer une sauvegarde et sélectionner **le fichier JSON privé de novembre** déjà préparé séparément. Ne **pas** mettre le JSON sur GitHub : il contient des informations financières personnelles. L'import remplace les données existantes et demande confirmation. Les transactions importées sont à confirmer comme payées ou non ; ne pas inventer leur statut.

Lorsqu'un import contient un solde initial, le premier mois disponible l'utilise comme solde de départ **à vérifier**. Un report explicite enregistré dans le mois a priorité. Les mois suivants n'importent pas automatiquement le report : le solde de départ peut être saisi manuellement dans le tableau mensuel, pour éviter de créer de faux soldes.

## Confidentialité

Tout est local (IndexedDB dans le navigateur). Aucun service bancaire, traqueur, clé API, compte obligatoire ni appel réseau pour les opérations courantes. Les données peuvent être perdues si les données Chrome sont effacées, en cas de changement de navigateur/téléphone, etc. Exporter régulièrement une sauvegarde. Les sauvegardes ne sont pas chiffrées : les conserver en lieu privé.

## Détails techniques

- `index.html` — structure et fenêtres de saisie.
- `style.css` — tableur responsive, navigation Samsung, thème clair.
- `app.js` — pages, édition, calculs d'affichage, import et mise à jour.
- `db.js` — conservation IndexedDB et sauvegardes, non réinitialisées.
- `budget.js` — formatage centimes, logique de base conservée.
- `sw.js` — cache isolé `mon-budget:<base>:v2.0.0`.
- `manifest.webmanifest` — identité installable stable.
- `icon-192.png`, `icon-512.png`, `apple-touch-icon.png` — logo portefeuille en marbre noir choisi.

Les frais de consommation, dettes et épargne sont séparés dans les tableaux selon le type/nom et l'éventuelle rubrique affectée. Les anciennes opérations ne sont **pas transformées automatiquement** ; une vérification est nécessaire si un remboursement, transfert ou une épargne était initialement saisi comme dépense.

## Vérifications

- Syntaxe JS (`node --check`) : OK.
- Tests de navigation, ajout/modification, paiement, catégorie et affichage sur largeurs 390px et 1330px : OK dans un navigateur de test avec stockage simulé.
- Affichage et passage de novembre à décembre avec 36 lignes d'import privé : OK dans un navigateur de test ; reprise de 20 charges fixes/crédits.
- Intégrité de l'archive ZIP et validité JSON du manifeste : vérifiées.
- Non vérifiés : déploiement réel GitHub Pages, cycle complet du service worker sur site HTTPS, appareil Samsung réel, persistance IndexedDB sur Samsung.

La V2 est une application indépendante fondée sur les fonctionnalités publiquement documentées de suivi du budget, **pas une copie exacte d'un modèle FocusDaily sous licence**.
