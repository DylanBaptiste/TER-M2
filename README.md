# TER-M2


L’objectif est de créer un modèle NLP basé sur un modèle pré-entraîné capable de
déterminer si un message français sur twitter relève du domaine de l’observation
d’un agriculteur ou non.

Architectutre en phase d'entrainement:

![Architectutre en phase d'entrainement](./src/Architectutre_Entrainement.jpg)

Architectutre en phase d'utilisation (inférence):

![Architectutre en phase d'utilisation](./src/Architecture_Utilisation.jpg)


Entrainement de 4 modeles diffirents, le model M1 qui predit à T+1 dans le futur, le model M2 qui predit à de T+1 à T+2 etc... jusque M4 qui predit de T+1 à T+4
Pour chaque modele Mi on recupere les accuracy de la prediction de T+1 à T+i
Par exemple pour le modele:
     M1 (qui predit T+1) on a l'accuracy T+1
     M2 (qui predit T+1, T+2) on à l'accuracy T+1 et T+2
     M3 (qui predit de T+1 à T+3) on à l'accuracy T+1, T+2 et T+3
     M4 (qui predit de T+1 à T+4) on à l'accuracy T+1, T+2, T+3 et T+4
     
l'accuracy T+1 est donc mesurée chez le model M4, M3, M2 et M1
l'accuracy T+2 est donc mesurée chez le model M4, M3 et M2
l'accuracy T+3 est donc mesurée chez le model M4 et M3
l'accuracy T+4 est donc mesurée chez le model M4

Chaque modele est entrainé en validation croisée (3 folds)
