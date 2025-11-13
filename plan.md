# Plan du TP - Prédiction des Prix AirBnB

## Objectif

Développer un modèle d'intelligence artificielle pour prédire les prix des logements AirBnB à partir du dataset `listings.csv`.

---

## 1. Collecte des Données

**Question 1.1** : Charger le fichier `listings.csv` en utilisant pandas. Combien de lignes et de colonnes contient le dataset ?

**Question 1.2** : Afficher les 5 premières lignes du dataset pour avoir un aperçu des données.

**Question 1.3** : Quelles sont toutes les colonnes disponibles dans le dataset ?

---

## 2. Prétraitement des Données

### 2.1 Sélection des colonnes

**Question 2.1** : Parmi les 18 colonnes disponibles, quelles sont celles qui semblent les plus pertinentes pour prédire le prix d'un logement ?

**Question 2.2** : Créer un nouveau DataFrame contenant uniquement les colonnes pertinentes suivantes :

- `room_type` (type de logement)
- `neighbourhood` (quartier)
- `latitude` et `longitude` (localisation)
- `minimum_nights` (durée minimum de séjour)
- `number_of_reviews` (nombre d'avis)
- `reviews_per_month` (avis par mois)
- `calculated_host_listings_count` (nombre de logements de l'hôte)
- `availability_365` (disponibilité sur l'année)
- `number_of_reviews_ltm` (avis des 12 derniers mois)
- `price` (variable cible)

### 2.2 Suppression des doublons

**Question 2.3** : Combien de lignes dupliquées existent dans le dataset ?

**Question 2.4** : Supprimer les lignes dupliquées si elles existent.

### 2.3 Gestion des valeurs manquantes

**Question 2.5** : Pour chaque colonne sélectionnée, quel est le nombre de valeurs manquantes ?

**Question 2.6** : Pour les colonnes numériques (`number_of_reviews`, `reviews_per_month`, etc.), remplacer les valeurs manquantes par la moyenne de la colonne.

**Question 2.7** : Pour la colonne `price`, que faire des valeurs manquantes ? Faut-il les supprimer ou les imputer ?

### 2.4 Conversion des types de colonnes

**Question 2.8** : La colonne `price` est-elle de type numérique ? Si non, comment la convertir ?

**Question 2.9** : Vérifier que toutes les colonnes numériques sont bien de type `float` ou `int`.

---

## 3. Analyse Descriptive des Données

**Question 3.1** : Calculer les statistiques descriptives (moyenne, médiane, écart-type, min, max) pour la colonne `price`.

**Question 3.2** : Créer un graphique de dispersion (scatter plot) montrant la relation entre `number_of_reviews` et `price`. Que peut-on observer ?

**Question 3.3** : Créer un graphique en barres montrant le prix moyen par `room_type`. Quel type de logement est le plus cher en moyenne ?

**Question 3.4** : Créer un graphique de dispersion montrant la relation entre `availability_365` et `price`. Y a-t-il une corrélation ?

**Question 3.5** : Calculer la matrice de corrélation entre toutes les variables numériques. Quelles variables sont les plus corrélées avec le prix ?

---

## 4. Recodage des Colonnes

**Question 4.1** : La colonne `room_type` contient des valeurs catégorielles. Utiliser le Label Encoding ou One-Hot Encoding pour transformer cette colonne en valeurs numériques.

**Question 4.2** : Devriez-vous également encoder la colonne `neighbourhood` ? Pourquoi ?

---

## 5. Gestion des Valeurs Aberrantes

**Question 5.1** : Créer un boxplot (boîte à moustaches) pour visualiser la distribution de la colonne `price`. Y a-t-il des valeurs aberrantes ?

**Question 5.2** : Utiliser la méthode de l'intervalle interquartile (IQR) pour identifier les valeurs aberrantes dans la colonne `price`. Combien y en a-t-il ?

**Question 5.3** : Décider d'une stratégie pour gérer ces valeurs aberrantes :

- Les supprimer ?
- Les plafonner (capping) ?
- Utiliser une transformation (MinMaxScaler, StandardScaler) ?

**Question 5.4** : Appliquer la transformation MinMaxScaler sur la colonne `price`. Quelles sont les valeurs minimum et maximum après transformation ?

---

## 6. Séparation des Données

**Question 6.1** : Séparer le dataset en variables explicatives (X) et variable cible (y).

- X : toutes les colonnes sauf `price`
- y : uniquement `price`

**Question 6.2** : Utiliser `train_test_split` de sklearn pour séparer les données en ensemble d'entraînement (60%) et ensemble de test (40%).

**Question 6.3** : Afficher la taille de chaque ensemble (nombre de lignes).

---

## 7. Modélisation - Régression Linéaire Simple

**Question 7.1** : Créer un modèle de régression linéaire simple qui prédit `price` uniquement en fonction de `number_of_reviews`.

**Question 7.2** : Entraîner le modèle sur l'ensemble d'entraînement.

**Question 7.3** : Calculer le score R² (coefficient de détermination) sur l'ensemble de test. Que signifie ce score ?

**Question 7.4** : Créer une visualisation montrant :

- Les points de l'ensemble d'entraînement
- Les points de l'ensemble de test
- La droite de régression

---

## 8. Modélisation - Régression Linéaire Multiple

**Question 8.1** : Créer un modèle de régression linéaire multiple qui prédit `price` en fonction de plusieurs variables :

- `number_of_reviews`
- `reviews_per_month`
- `availability_365`
- `room_type` (encodé)

**Question 8.2** : Entraîner le modèle sur l'ensemble d'entraînement.

**Question 8.3** : Calculer le score R² sur l'ensemble de test. Est-il meilleur que celui de la régression simple ?

**Question 8.4** : Faire des prédictions sur l'ensemble de test et calculer l'erreur moyenne (MAE - Mean Absolute Error) et l'erreur quadratique moyenne (RMSE - Root Mean Squared Error).

**Question 8.5** : Créer une visualisation 3D montrant la relation entre 2 variables explicatives et le prix prédit.

---

## 9. Amélioration du Modèle (Optionnel)

**Question 9.1** : Tester d'autres algorithmes de régression :

- Random Forest Regressor
- Gradient Boosting Regressor
- Ridge ou Lasso Regression

**Question 9.2** : Comparer les performances (R², MAE, RMSE) de tous les modèles. Quel est le meilleur ?

**Question 9.3** : Pour le meilleur modèle, quelles sont les variables les plus importantes pour prédire le prix ?

---

## 10. Conclusion

**Question 10.1** : Résumer les résultats obtenus. Quel modèle recommanderiez-vous pour prédire les prix AirBnB ?

**Question 10.2** : Quelles sont les limitations de votre modèle ? Comment pourrait-on l'améliorer ?

**Question 10.3** : Si vous deviez déployer ce modèle en production, quelles seraient les prochaines étapes ?
