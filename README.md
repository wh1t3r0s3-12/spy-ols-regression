# Econometrie Projet

> Modélisation par régression linéaire multiple (OLS) du rendement du SPY à partir de plusieurs actifs et taux, avec diagnostic complet du modèle.

## Objectif

Expliquer le rendement journalier du SPY (ETF répliquant le S&P 500) par un modèle de régression linéaire multiple utilisant les rendements d'autres actifs et instruments financiers (action AAPL, taux de change USD/CNY, taux court terme, or, etc.), puis valider la robustesse du modèle via une série de tests économétriques.

## Données

Le dossier [`data/`](data/) contient les séries de prix utilisées pour construire le modèle :

| Fichier | Description |
|---|---|
| `Données SPY.csv` | Prix de l'ETF SPY (variable expliquée) |
| `AAPL.csv` | Prix de l'action Apple |
| `USD_CNY.csv` | Taux de change USD/Yuan |
| `Gold.csv` | Prix de l'or |
| `HIS.csv`, `DTB6.csv`, `TCD6.csv`, `DR5.xls`, `Taux_ST6.xls`, `VRV.xls` | Taux d'intérêt et instruments de taux court/moyen terme |

## Méthodologie

Le notebook ([`notebooks/notebook.ipynb`](notebooks/notebook.ipynb)) couvre :

1. **Préparation des données** : uniformisation des colonnes, conversion des dates, calcul des rendements journaliers, fusion des séries sur la date
2. **Régression OLS multiple** du rendement du SPY sur les rendements des autres actifs
3. **Diagnostic du modèle** :
   - Test de Rainbow (linéarité)
   - Analyse des résidus studentisés (homoscédasticité, normalité, Q-Q plot)
   - Détection des points aberrants et influents (résidus studentisés, levier, distance de Cook)
   - Facteur d'inflation de la variance (VIF) pour la multicolinéarité

Le rapport complet de l'analyse est disponible dans [`docs/rapport.docx`](docs/rapport.docx).

## Installation

```bash
git clone https://github.com/wh1t3r0s3-12/econometrie-projet.git
cd econometrie-projet
pip install -r requirements.txt
```

## Utilisation

```bash
jupyter notebook notebooks/notebook.ipynb
```
