# Turbofan Engine Anomaly Detection

## Description
Projet de détection d’anomalies sur des capteurs industriels, basé sur le **jeu de données NASA CMAPSS**. https://data.nasa.gov/dataset/cmapss-jet-engine-simulated-data 
L’objectif est de classifier si un moteur est en état **normal** ou **proche de la panne**, à partir des mesures issues de capteurs.

---

##  Données
- **Source** : NASA Turbofan Engine Degradation Simulation Data Set (CMAPSS)  
- **Sous-ensemble utilisé** : FD001  
- **Variables** :  
  - Identifiant du moteur  
  - Cycle de fonctionnement  
  - 3 paramètres opérationnels  
  - 21 capteurs  
- **Taille** : 20 631 observations  
- **Variable cible** :  
  - `target = 1` → moteur proche de la panne (RUL ≤ 30)  
  - `target = 0` → moteur normal  

---

## Méthodologie
1. **Nettoyage et normalisation des données**
   - Suppression des colonnes constantes  
   - Standardisation avec `StandardScaler`  

2. **Feature Engineering**
   - Calcul de la Remaining Useful Life (RUL)  
   - Création d’une variable binaire `target`  

3. **Visualisation**
   - PCA pour visualiser la variance et la répartition des classes  

4. **Modélisation**
   - Modèle utilisé : `MLPClassifier` (scikit-learn)  
   - Évaluation par matrice de confusion et score de précision  

---

##  Résultats
| Métrique | Valeur |
|-----------|---------|
| Accuracy | 0.96 |
| Confusion Matrix | [[3467, 66], [96, 497]] |

- Très bonne détection des moteurs normaux.  
- Quelques faux négatifs (moteurs anormaux non détectés).  

---

## Technologies
- Python  
- pandas, scikit-learn, matplotlib  

---

## Visualisations
Visualisation PCA (projection 2D) :
- Bleu → moteur normal  
- Rouge → proche panne  
- Répartition en “crête” décalée illustrant la dégradation progressive.

---

## Référence
> A. Saxena, K. Goebel, D. Simon, and N. Eklund (2008).  
> *Damage Propagation Modeling for Aircraft Engine Run-to-Failure Simulation.*  
> Proceedings of the 1st International Conference on Prognostics and Health Management (PHM08), Denver, CO.




