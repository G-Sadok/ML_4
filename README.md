# 🧥 Fashion MNIST Classification: Ensemble Learning & Random Forest

![Python](https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge&logo=python)
![Scikit-Learn](https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=for-the-badge&logo=python&logoColor=white)

## 📖 Aperçu du Projet

Ce projet explore les techniques de **Machine Learning Supervisé** et plus particulièrement l'**Ensemble Learning** (méthodes ensemblistes) pour classifier des images du dataset *Fashion MNIST*.

L'objectif est de dépasser les performances d'un modèle unique en combinant plusieurs modèles faibles (weak learners) via des techniques de **Bagging** et de **Random Forest**. [cite_start]Le dataset contient 70 000 images en niveaux de gris (28x28 pixels) réparties en 10 catégories de vêtements (T-shirt, Pantalon, Pullover, Robe, etc.) [cite: 68-70].


## 📂 Structure du Projet

Le projet est divisé en deux approches complémentaires :

* **`Ensemble Learning.ipynb`** : Implémentation générique du **Bagging Classifier**. Ce notebook teste la combinaison de divers algorithmes de base (KNN, Arbres de Décision, One-vs-Rest) encapsulés dans une stratégie de Bagging.
* **`Random Forest.ipynb`** : Focus spécifique sur l'algorithme des **Forêts Aléatoires** (Random Forest), qui est une implémentation optimisée du Bagging appliquée aux arbres de décision.

## 🛠️ Méthodologie et Fonctionnalités

### 1. Prétraitement et Analyse (`Ensemble Learning.ipynb`)
* **Analyse de Corrélation :** Étude de la corrélation entre les pixels et les labels cibles pour identifier les zones de l'image les plus déterminantes.
* **Standardisation :** Utilisation de `StandardScaler` pour normaliser les valeurs des pixels, étape cruciale pour les algorithmes basés sur la distance comme KNN.
* **Visualisation :** Affichage d'un échantillon d'images avec leurs labels réels pour vérifier l'intégrité des données.

### 2. Bagging Classifier
Utilisation de `BaggingClassifier` de Scikit-Learn pour améliorer la stabilité et la précision.
* **Modèles de base testés :**
    * K-Nearest Neighbors (KNN)
    * Decision Tree Classifier (DTC)
    * OneVsRest Classifier
* **Optimisation :** Recherche des meilleurs hyperparamètres (`n_neighbors`, `max_depth`) via `GridSearchCV`.
* **Expérimentation :** Comparaison des performances en faisant varier le nombre d'estimateurs (`n_estimators` = 2, 4, 5, 8).


### 3. Random Forest (`Random Forest.ipynb`)
* **Modélisation :** Entraînement d'un modèle `RandomForestClassifier`.
* **Tuning :** Boucle d'optimisation pour tester l'influence du nombre d'arbres (`n_estimators` : 10, 50, 100) sur la précision globale.
* **Évaluation :** Analyse détaillée via :
    * Score de Précision et de Rappel (Macro Average).
    * **Matrice de Confusion** pour visualiser les erreurs de classification entre des classes similaires (ex: T-Shirt vs Shirt).

## 📊 Résultats Clés

* L'approche **Random Forest** s'est avérée plus robuste et rapide à converger que le Bagging manuel de KNN.
* L'augmentation du nombre d'arbres (de 10 à 100) améliore la précision, stabilisant le modèle autour d'un score performant (ex: ~88% de précision avec 100 arbres).

## 🚀 Installation et Utilisation

1.  **Cloner le dépôt :**
    ```bash
    git clone [https://github.com/ton-user/fashion-mnist-ensemble.git](https://github.com/ton-user/fashion-mnist-ensemble.git)
    cd fashion-mnist-ensemble
    ```

2.  **Installer les dépendances :**
    ```bash
    pip install pandas numpy matplotlib seaborn scikit-learn jupyter
    ```

3.  **Lancer les Notebooks :**
    ```bash
    jupyter notebook "Ensemble Learning.ipynb"
    jupyter notebook "Random Forest.ipynb"
    ```

---

## 🇬🇧 English Summary

**Project:** Fashion MNIST Classification using Ensemble Learning

**Goal:** Classify clothing images using Ensemble methods to improve predictive performance over single algorithms.

**Key Features:**
* **Generic Bagging:** Implemented `BaggingClassifier` wrapping KNN, Decision Trees, and OneVsRest models. Included GridSearch for hyperparameter tuning.
* **Random Forest:** Specialized implementation exploring the effect of increasing `n_estimators` (trees) on model accuracy.
* **Data Processing:** Pixel correlation analysis and Standardization (`StandardScaler`).
* **Evaluation:** Detailed metrics including Confusion Matrices, Precision, and Recall scores.

**Tech Stack:** Python, Scikit-Learn, Pandas, Seaborn.
