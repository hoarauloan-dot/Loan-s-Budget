# Mon Budget — V1.0.0
Application PWA personnelle, locale, en français, adaptée à Chrome Android et aux navigateurs récents. Aucun compte bancaire connecté, aucun serveur de stockage et aucune synchronisation entre appareils.

## Installer sur GitHub Pages
1. Décompresser le ZIP.
2. Créer un dépôt GitHub, par exemple `mon-budget`.
3. Ajouter **le contenu du dossier** à la racine du dépôt (pas le dossier lui-même), puis `Commit changes`.
4. `Settings` → `Pages` → `Deploy from a branch` → branche `main`, dossier `/ (root)` → `Save`.
5. Ouvrir `https://VOTRE-NOM.github.io/mon-budget/` dans Chrome sur le Samsung.
6. Menu Chrome → `Ajouter à l'écran d'accueil` / `Installer l'application`.
7. Ouvrir l'application en ligne une fois, puis tester le mode avion.
8. `Paramètres` → `Exporter une sauvegarde` pour créer une sauvegarde JSON régulière.
9. Pour une nouvelle version : remplacer les fichiers, mettre à jour `VERSION`/`CACHE` de `sw.js`, publier puis `Paramètres` → `Rechercher les mises à jour`.

## Importer les données préparées depuis Excel
Le fichier séparé `import-prive-novembre-2026.json` **n'est pas dans ce ZIP** : ne l'ajoutez **jamais** à GitHub. Sur le Samsung, ouvrez `Paramètres` → `Importer une sauvegarde` et sélectionnez ce fichier **avant d'ajouter d'autres données**. Examinez les informations dans l'application et confirmez les montants. Les colonnes de l'Excel n'indiquent pas de manière certaine quels paiements ont été effectivement débités : les opérations sont donc initialement marquées `À payer` ou `À recevoir` par prudence. Le `solde 2 775 €` est traité comme solde d'ouverture à vérifier et non comme salaire encaissé. Les versements d'épargne sont des transferts et non des dépenses de consommation.

## Confidentialité et limites
Le **code** déposé sur GitHub est public. Les **données** saisies restent dans IndexedDB sur le navigateur de l'appareil, sauf export volontaire. Elles ne sont **pas chiffrées**. Elles peuvent être perdues si le stockage du navigateur est effacé, si le téléphone est perdu ou si vous changez d'origine GitHub Pages. Ne communiquez pas les fichiers de sauvegarde. Le stockage est indépendant par navigateur/appareil : aucun partage automatique entre Samsung et iPhone.

## Calculs
Montants stockés en centimes entiers. Dépense `payée` = déduite du solde réel estimé ; prévue = prise en compte dans la prévision seulement. Les transferts ne sont jamais classés comme dépenses de consommation. Le solde affiché est un **solde calculé**, exact uniquement si les soldes initiaux et les opérations sont complets. Un revenu n'est pas assimilé automatiquement à un solde d'ouverture.

## Import / restauration
L'import **remplace** les données du navigateur après vérification et confirmation. Faire un export préalable. La restauration utilise une transaction IndexedDB multi-magasins atomique. Ne pas confondre ce mécanisme avec une garantie de sauvegarde externe.

## Vérifications et limites de test
Fichiers JS et JSON soumis à vérification de syntaxe à la livraison. Aucune validation physique sur téléphone Samsung ni audit complet multi-navigateurs n'a été effectuée. L'installation, le mode hors ligne, les dialogues, les exports et la mise à jour doivent être testés sur l'appareil cible avant un usage quotidien.
