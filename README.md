Projet de Reconnaissance des Formes Géométriques

Ce projet vise à créer un modèle de réseau de neurones pour la reconnaissance des formes géométriques (carré, cercle, triangle isocèle, et triangle rectangle) à partir d'images. Le modèle est entraîné en utilisant TensorFlow et Keras, et une application Web est développée pour tester le modèle.
Table des Matières

    Prérequis
    Installation
    Prétraitement des Données
    Entraînement du Modèle
    Test et Prédiction
    Déploiement de l'Application Web
    Structure du Projet
    Contact

Prérequis

Avant de commencer, assurez-vous d'avoir installé les outils suivants :

    Python 3.7 ou supérieur
    pip (gestionnaire de paquets Python)
    Virtualenv (optionnel mais recommandé)

Installation

Clonez ce dépôt sur votre machine locale :

sh

git clone https://github.com/votre-utilisateur/votre-repo.git
cd votre-repo

Créez un environnement virtuel (optionnel mais recommandé) :

sh

python3 -m venv env
source env/bin/activate  # Pour Linux/Mac
env\Scripts\activate  # Pour Windows

Installez les dépendances requises :

sh

pip install -r requirements.txt

Prétraitement des Données

Les données doivent être organisées en répertoires, avec un répertoire pour chaque classe. Par exemple :

kotlin

data/
├── carre/
│   ├── image1.jpg
│   ├── image2.jpg
│   └── ...
├── cercle/
│   ├── image1.jpg
│   ├── image2.jpg
│   └── ...
├── triangle_iso/
│   ├── image1.jpg
│   ├── image2.jpg
│   └── ...
└── triangle_rect/
    ├── image1.jpg
    ├── image2.jpg
    └── ...

Exécutez le script de prétraitement des données pour convertir les images en un format exploitable par le modèle :

sh

python preprocess_data.py

Ce script va lire les images, les convertir en niveaux de gris, appliquer des améliorations de contraste et de netteté, les redimensionner à 28x28 pixels, et les enregistrer dans un fichier .npz nommé preprocessed_images.npz.
Entraînement du Modèle

Pour entraîner le modèle, exécutez le script train_model.py :

sh

python train_model.py

Ce script charge les données prétraitées à partir de data/preprocessed_images.npz, divise les données en ensembles d'entraînement, de validation et de test, et entraîne un modèle de réseau de neurones MLP (Perceptron Multicouche).
Test et Prédiction

Pour tester le modèle sur de nouvelles images et obtenir des prédictions, utilisez le script test_model.py :

sh

python test_model.py --image chemin/vers/image.jpg

Ce script charge le modèle entraîné, prétraite l'image fournie et affiche la prédiction.
Déploiement de l'Application Web

Pour déployer l'application Web qui permet de tester le modèle via une interface utilisateur, vous devez installer Shiny pour Python :

sh

pip install shiny

Ensuite, exécutez l'application avec la commande suivante :

sh

shiny run --reload app.py

Ouvrez votre navigateur et allez à l'adresse http://localhost:8000 pour accéder à l'application.
Structure du Projet

kotlin

votre-repo/
├── data/
│   ├── carre/
│   ├── cercle/
│   ├── triangle_iso/
│   └── triangle_rect/
├── models/
│   └── modele_pml.h5
├── preprocess_data.py
├── train_model.py
├── test_model.py
├── app.py
├── requirements.txt
└── README.md

    data/ : Dossier contenant les images des différentes classes.
    models/ : Dossier contenant les modèles entraînés.
    preprocess_data.py : Script pour le prétraitement des données.
    train_model.py : Script pour l'entraînement du modèle.
    test_model.py : Script pour tester le modèle sur des images individuelles.
    app.py : Script de l'application Web Shiny.
    requirements.txt : Liste des dépendances Python.
    README.md : Ce fichier.


