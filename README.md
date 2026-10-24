# PI² n°183 — Estimation robuste du risque et optimisation de portefeuille

Équipe P183_T3 (ESILV) — partenaire : M. Attali — tuteur : M. Heranval

## Contenu du dépôt

| Dossier | Ce qu'il y a dedans |
|---|---|
| `data/` | **Pas sur GitHub** (voir plus bas) : à créer soi-même sur son ordinateur |
| `notebooks/` | Les notebooks de chacun |
| `resultats/` | Fichiers produits par les notebooks (poids, graphiques, tableaux) |

## Les données (à faire une fois, chacun de son côté)

Les données de M. Attali ne sont **pas mises sur GitHub** (car le dépôt est public).
Chacun doit :

1. créer un dossier `data/` à côté des dossiers `notebooks/` et `resultats/` ;
2. y mettre le fichier Excel des données (celui envoyé sur le groupe), renommé **`Data_SP.xlsx`**.

Ce fichier contient les prix journaliers des 24 indices sectoriels du S&P 500 et du S&P 500 lui-même (SPX), de 1992 à 2024. Ne pas le modifier.

**Attention :** ne jamais envoyer le dossier `data/` sur GitHub, même par erreur.

## Ce qui est déjà fait

- `notebooks/min_variance_empirique.ipynb` : portefeuille de variance minimale avec la matrice de covariance empirique, rebalancement mensuel, fenêtre d'un an. Comparaison avec le S&P 500.
- `resultats/Historique_Poids_Secteurs_empirique.xlsx` : historique des poids par secteur (en %) obtenu avec ce notebook.

## Qui fait quoi

| Partie | Qui | Branche |
|---|---|---|
| Variance minimale, matrice empirique | (fait) | `main` |
| Matrice de Ledoit-Wolf | Clémence | `ledoit-wolf` |
| Backtests de base + comparaison avec la méthode empirique | Clémence | `backtests` |
| Méthode EWMA | à compléter | `ewma` |

## Règle commune pour les méthodes

Chaque méthode d'estimation (empirique, Ledoit-Wolf, EWMA…) doit pouvoir s'écrire comme une fonction qui :

- **prend** un tableau de rendements (une ligne par jour, une colonne par secteur) sur la fenêtre d'estimation ;
- **renvoie** la matrice de covariance (secteurs × secteurs).

Comme ça, pour passer d'une méthode à l'autre dans le backtest, on change juste la fonction appelée. Dans le notebook empirique, c'est l'endroit où il y a `sub_returns.cov().values`.

## Comment on travaille avec GitHub

1. **`main`** = la version commune qui marche. On ne travaille pas directement dessus.
2. Chacun travaille sur **sa branche** (voir le tableau au-dessus).
3. Quand un morceau marche, on fait une **pull request** (demande de fusion) vers `main`, un autre membre jette un œil, puis on fusionne.

Pour lancer un notebook : ouvrir le dossier `notebooks/` dans Jupyter / VS Code. Les chemins vers les données sont écrits en `../data/...`, donc il faut que le notebook reste dans le dossier `notebooks/`.

Bibliothèques Python nécessaires : `pandas`, `numpy`, `matplotlib`, `openpyxl` (pour lire les fichiers Excel).
