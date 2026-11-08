# Mon Budget V1.2.0 — Suivi mensuel simple

## Installation / mise à jour
1. **Sur PC**, décompresser cette archive, puis déposer ses fichiers à la racine du dépôt GitHub Pages existant. Valider le commit.
2. Attendre que le déploiement GitHub Pages soit terminé.
3. Sur le Samsung, ouvrir Mon Budget > Réglages > Rechercher les mises à jour. Si disponible, choisir Charger / Installer la nouvelle version. Un rechargement normal peut aussi être nécessaire.
4. Vérifier la version 1.2.0 dans Réglages.

**Le bouton de mise à jour ne transfère pas le ZIP vers GitHub.** La publication sur GitHub doit être faite avant de cliquer dans l'application.

## Usage simple
- **Mon mois** : revenus et dépenses du mois, part payée, rubriques automatiques.
- **Dépenses** : appuyer sur une ligne pour modifier, payer, copier ou reporter.
- **Prévisions** : budgets par catégories et charges récurrentes.
- **Épargne** : coffres et transferts.
- **Bilan** : suivi et graphiques.
- **Réglages** : sauvegarder, importer, vérifier la version.

Les chiffres restent stockés localement dans IndexedDB `mon-budget-db`, qui conserve le même nom et le même schéma qu'en V1.1.0. Aucune donnée privée dans ce ZIP. Une sauvegarde JSON est conseillée **avant** la mise à jour. Ne pas désinstaller l'application ni effacer les données du site.

## Design
Interface originale inspirée de la structure générale des tableaux de budget (présentation mensuelle, 4 indicateurs, lignes de dépenses, bilan). Il ne s'agit pas du template FocusDaily original.

## Vérifications
Contrôles de syntaxe et des fichiers du ZIP possibles en local; utilisation Android et migration réelle à confirmer sur le téléphone.
