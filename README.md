
## Classification des caractères Tifinagh à l’aide d’un réseau neuronal multiclasses
### Introduction
La reconnaissance de caractères manuscrits constitue un défi majeur en vision par ordinateur, en particulier pour les systèmes d’écriture moins étudiés comme le Tifinagh, utilisé par les communautés amazighes. Contrairement aux écritures largement étudiées telles que le latin ou l’arabe, la nature géométrique et non cursive du Tifinagh nécessite des approches spécialisées. Ce projet met en œuvre un réseau neuronal multiclasses, de type perceptron multicouche (MLP), pour classer les caractères Tifinagh, en adaptant des techniques issues de la classification binaire à un cadre comportant 33 classes distinctes.

La base de données Amazigh Handwritten Character Database (AMHCD) fournit 28 182 images en niveaux de gris (64x64 pixels), redimensionnées à 32x32 pixels et aplaties en vecteurs de 1024 dimensions. Le MLP, doté de deux couches cachées de 64 et 32 neurones, utilise des fonctions d’activation ReLU et une couche de sortie softmax. L’objectif de cette étude est d’atteindre une précision élevée, en incorporant une régularisation L2 et en explorant l’optimiseur Adam pour améliorer les performances, contribuant ainsi au développement de systèmes OCR robustes pour l’écriture Tifinagh.

## Méthodologie
### Jeu de données
Le jeu de données AMHCD contient 28 182 images en niveaux de gris de caractères Tifinagh manuscrits (64x64 pixels), réparties en 33 classes représentant les lettres de l’alphabet Tifinagh [1]. Collectées auprès de 60 scripteurs, ces images reflètent une grande variabilité dans les styles d’écriture. Les images ont été redimensionnées à 32x32 pixels, converties en niveaux de gris, normalisées dans l’intervalle [0,1], puis aplaties en vecteurs de 1024 dimensions.

Une normalisation spécifique a été appliquée au caractère ‘ya’ (ⴰ) afin de le différencier de ‘yar’ (ⵔ), en ajoutant un espace vide pour réduire la confusion liée à leur forme circulaire [1]. Le jeu de données a été divisé par échantillonnage stratifié en ensembles d’entraînement (60 %), de validation (20 %) et de test (20 %) pour assurer une représentation équilibrée des classes.
### Télécharger la base de données : https://drive.google.com/file/d/1g03sIzi8F855KRMi0wmJesdiVQe219nY/iew?usp=share_link
### Architecture du modèle
Le réseau de neurones MLP est conçu comme suit :

Couche d’entrée : 1024 neurones (images aplaties de 32x32).

Couches cachées : deux couches comportant respectivement 64 et 64 neurones, avec activation ReLU, définie par :


## Prétraitement et apprentissage
Les images ont été prétraitées avec OpenCV (redimensionnement et normalisation), et les étiquettes encodées en one-hot via OneHotEncoder. L’apprentissage s’est effectué sur 100 époques avec un batch de 32, un taux d’apprentissage de 0.01, et une régularisation L2 

L’optimiseur Adam a été utilisé avec les paramètres :
 
## Évaluation
L’évaluation du modèle a inclus :

Précision globale : proportion d’images correctement classées.

Rapport de classification : précision, rappel, et F1-score par classe.

Matrice de confusion : pour identifier les erreurs de classification.

Courbes de perte et de précision : pour évaluer la convergence du modèle.

## Implémentation
Le modèle a été implémenté en Python à l’aide des bibliothèques : NumPy, OpenCV, scikit-learn, Matplotlib et Seaborn.
Le code est disponible ici : [Lien  GitHub].

### Résultats
Le MLP a atteint une précision de test d’environ 85 % après 100 époques. Le rapport de classification montre une forte précision pour la majorité des classes, bien que des confusions soient observées entre ‘ya’ (ⴰ) et ‘yar’ (ⵔ), en raison de leurs formes circulaires similaires [1]. La matrice de confusion (Figure 1) illustre ces erreurs. Les courbes de perte et de précision (Figure 2) indiquent une convergence stable, avec une perte de validation proche de celle d’entraînement, suggérant un surapprentissage limité.

L’optimiseur Adam a permis une convergence plus rapide que SGD, et la régularisation L2 a amélioré la généralisation en limitant la magnitude des poids.




Télécharger la base de données : https://drive.google.com/file/d/1g03sIzi8F855KRMi0wmJesdiVQe219nY/
view?usp=share_link

