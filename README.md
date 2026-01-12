# Credit Scoring – Prédiction du défaut de paiement

##  Objectif du projet
L’objectif de ce projet est de construire un **modèle de scoring crédit** permettant de prédire la **probabilité de défaut de paiement** d’un client à partir de données socio-économiques et financières.  
Ce type de modèle est largement utilisé en **banque** et en **assurance** pour appuyer les décisions d’octroi de crédit et la gestion du risque.

---

##  Données
- **Source** : German Credit Dataset (Kaggle / UCI)
- **Taille** : 1 000 observations
- **Variables** : 21 variables explicatives
- **Cible** :  
  - `0` -> client sans défaut  
  - `1` -> client en défaut  

Les données décrivent à la fois :
- le **crédit** (montant, durée, charge de remboursement, etc.)
- le **profil du client** (âge, situation professionnelle, historique de crédit, etc.)

---

##  Méthodologie

Le projet suit l’ensemble du **cycle de vie d’un projet de data science** :

### 1️.- Analyse exploratoire des données (EDA)
- Analyse descriptive
- Étude de la variable cible
- Visualisation des relations entre variables et défaut
- Analyse des distributions et des valeurs aberrantes

### 2️.- Nettoyage des données
- Vérification des valeurs manquantes et des doublons
- Analyse des outliers via la méthode IQR  
- Conservation des valeurs aberrantes jugées pertinentes d’un point de vue métier

### 3️.- Préparation des données
- Séparation variables explicatives / cible
- Split **train / test** avec stratification
- Encodage des variables catégorielles (One-Hot Encoding)
- Normalisation des variables numériques
- Pipeline de prétraitement pour éviter toute fuite d’information

### 4️.- Modélisation
- **Modèle baseline** : Régression logistique (pondération des classes)
- **Modèle comparatif** : Random Forest
- Prédiction de probabilités de défaut

### 5️.- Évaluation
- Matrice de confusion
- Precision, Recall, F1-score
- ROC-AUC
- Analyse orientée **risque métier** (faux négatifs vs faux positifs)

---

##  Résultats

| Modèle | ROC-AUC | Recall défaut (1) | Precision défaut (1) |
|------|--------|-------------------|----------------------|
| Régression logistique | ~0.81 | 0.80 | 0.56 |
| Random Forest | ~0.80 | 0.70 | 0.60 |

- Les deux modèles présentent un **bon pouvoir discriminant**
- La **régression logistique** détecte mieux les clients en défaut (rappel plus élevé)
- Le **Random Forest** est légèrement plus précis mais moins interprétable

---

##  Conclusion métier
La **régression logistique** a été retenue comme **modèle final**, car elle offre :
- un **bon rappel sur les clients en défaut**
- une **interprétabilité élevée**, essentielle dans un contexte bancaire réglementé
- un excellent compromis entre performance et transparence

Ce modèle peut être utilisé comme un **outil d’aide à la décision**, permettant de prioriser les dossiers à risque et de renforcer la gestion du risque de crédit.

---

##  Perspectives d’amélioration
- Ajustement du seuil de décision selon les coûts métier
- Test de modèles plus avancés (Gradient Boosting, XGBoost)
- Intégration de données comportementales supplémentaires
- Analyse coût-bénéfice des erreurs de classification

---

##  Technologies utilisées
- Python
- Pandas, NumPy
- Scikit-learn
- Matplotlib, Seaborn
- Jupyter Notebook

---

##  Auteur
Projet réalisé par Laveus Mick-Wanderly
Étudiant en mathématiques & informatique – spécialisation data  
Intéressé par les métiers de la **data science en finance et assurance**
