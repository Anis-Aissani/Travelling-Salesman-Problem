
# 🌍 TSP Solver Suite : Comparaison d'Algorithmes

Ce projet implémente et compare plusieurs algorithmes pour résoudre le célèbre **Problème du Voyageur de Commerce (Traveling Salesperson Problem - TSP)**.

L'objectif est d'étudier le compromis entre la **précision** (qualité de la solution) et la **performance** (temps de calcul) à travers quatre approches différentes, allant de l'heuristique gloutonne à la solution exacte.

## 🚀 Fonctionnalités

* **Génération de données :** Création de graphes aléatoires ou lecture depuis un fichier texte.
* **Visualisation :** Affichage graphique des cycles trouvés avec `matplotlib`.
* **Analyse Statistique :** Comparaison sur 100 essais (moyennes, écarts-types, gains en %).
* **Étude de Complexité :** Courbes d'évolution du temps et du coût en fonction du nombre de villes ($N$).

## 🧠 Les Algorithmes Implémentés

### 1. PPP (Plus Proche Voisin)
- **Type :** Heuristique Gloutonne (Constructive)
- **Principe :** On va toujours à la ville non visitée la plus proche
- **Complexité :** Très rapide, mais résultat souvent médiocre

### 2. OptPPP (2-Opt)
- **Type :** Recherche Locale (Amélioration)
- **Principe :** Part du résultat de PPP et "démêle" les croisements en inversant des sections du chemin
- **Performance :** Excellent compromis temps/qualité

### 3. OptPrim (Approximation via MST)
- **Type :** Approximation garantie (2-Approx)
- **Principe :** Construit un Arbre Couvrant Minimum (MST) avec Prim, puis effectue un parcours en profondeur (DFS)
- **Garantie :** La solution est garantie d'être au pire 2 fois l'optimal

### 4. HDS (Heuristique Demi-Somme)
- **Type :** Exact (Branch & Bound)
- **Principe :** Explore l'arbre des solutions en utilisant une borne inférieure (Demi-Somme des 2 meilleures arêtes) pour élaguer les branches inutiles
- **Performance :** Donne la solution **optimale**, mais le temps explose quand $N > 15$

## 📦 Structure du Projet

```
TSP-Solver-Suite/
├── README.md
├── data/
└── src/
    ├── main.py                 # Point d'entrée principal (Menu)
    ├── plot.py                 # Affichage matplotlib
    ├── statistics.py           # Analyses statistiques
    ├── utils.py                # Fonctions utilitaires
    ├── algos/
    │   ├── algo_ppp.py         # Plus Proche Voisin
    │   ├── opt_ppp.py          # Optimisation 2-Opt
    │   ├── opt_prim.py         # Approximation MST + DFS
    │   └── hds.py              # Branch & Bound (Exact)
    └── structures/
        ├── __init__.py
        ├── graphe_md.py        # Représentation du graphe (Matrice)
        ├── graphe_tl.py        # Représentation du graphe (Liste)
        ├── noeud_exploration.py # Nœud d'exploration B&B
        └── tas.py              # File de priorité (Tas)
```

## 🛠️ Installation et Exécution

### Prérequis

- Python 3.x
- Matplotlib (pour les graphiques)
- Numpy (pour les calculs matriciels)
- PyQt5 (pour le GUI)

```bash
pip install matplotlib numpy PyQt5
```

### Lancer le projet

Exécutez simplement le fichier `main.py` à la racine :

```bash
python main.py
```

## 📊 Utilisation

Une fois lancé, le programme propose 3 modes :

### 1. Démonstration Visuelle
- Lance les 4 algorithmes sur un seul graphe (aléatoire ou fichier)
- Affiche les 4 cycles trouvés côte à côte pour comparer visuellement

### 2. Étude Statistique (100 Essais)
- Génère 100 graphes de taille N
- Affiche un tableau récapitulatif (Moyennes, Temps, Gains en %)
- Affiche des histogrammes et boîtes à moustaches (boxplots)
- *Idéal pour valider la robustesse des algorithmes*

### 3. Étude d'Évolution (Complexité)
- Fait varier N (ex: 5, 7, 9, 11, 13...)
- Trace les courbes de temps (échelle logarithmique) et de coût
- *Idéal pour visualiser l'explosion exponentielle de l'algo exact (HDS)*

## 📝 Auteur

Anis AISSANI

