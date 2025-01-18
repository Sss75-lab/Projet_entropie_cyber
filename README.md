### **README : Génération de nombres basés sur l'entropie d'une image**

---

## **Description**
Ce script Python permet de générer un **grand nombre entier** basé sur l'entropie d'une image en :
1. Transformant l'image en données de pixels.
2. Calculant un hachage cryptographique unique (SHA-256) de ces données.
3. Produisant un nombre d'une longueur spécifiée à partir de ce hachage.

Le script prend en charge des **arguments en ligne de commande** pour personnaliser le chemin de l'image, les dimensions de redimensionnement, et la longueur du nombre généré.

---

## **Utilité dans la cybersécurité**
Ce code peut être utilisé pour **générer des nombres uniques et reproductibles** à partir d'une image. Ces nombres peuvent servir dans divers contextes de cybersécurité, par exemple :

- **Clés de chiffrement** : Générer une clé unique pour protéger des données sensibles.
- **Jetons d'identification** : Créer des identifiants uniques pour des utilisateurs ou des sessions.
- **Sources d'entropie** : Fournir une base pour des générateurs de nombres pseudo-aléatoires dans des systèmes sécurisés.

### **Exemple d'application : Génération d'une clé unique**
Dans un système de chiffrement personnalisé, une image peut servir de "graine" pour générer une clé de chiffrement unique. Tant que la même image est utilisée, la clé peut être reproduite, garantissant une gestion sécurisée sans stocker directement la clé.

---

## **Prérequis**
- Python 3.x installé.
- Bibliothèques Python requises :
  - **Pillow** : Pour manipuler les images.
  - **argparse** : Pour gérer les arguments en ligne de commande (inclus par défaut dans Python).
  - **hashlib** : Pour calculer les hachages cryptographiques (inclus par défaut dans Python).

### **Installation des dépendances**
Si Pillow n'est pas installé, exécutez :
```bash
pip install pillow
```

---

## **Utilisation**
### **1. Lancer le script**
Pour exécuter le script, utilisez la commande suivante dans un terminal :
```bash
python script.py <chemin_de_l_image> [--size largeur hauteur] [--length longueur]
```

### **2. Arguments**
- **`<chemin_de_l_image>`** (obligatoire) : Spécifie le chemin de l'image à traiter.
- **`--size largeur hauteur`** (optionnel) : Définit les dimensions de redimensionnement de l'image (par défaut : `100x100`).
- **`--length longueur`** (optionnel) : Définit la longueur du nombre généré (par défaut : `20`).

---

### **3. Exemples**

#### **Exemple 1 : Utilisation de base**
```bash
python script.py image.png
```
- Génère un nombre de 20 chiffres basé sur l'image `image.png`.

#### **Exemple 2 : Personnalisation de la taille et de la longueur**
```bash
python script.py image.png --size 200 200 --length 50
```
- Redimensionne l'image à 200x200 pixels.
- Génère un nombre de 50 chiffres.

#### **Exemple 3 : Image introuvable**
Si l'image spécifiée n'existe pas :
```bash
python script.py fichier_inexistant.png
```
- Affiche : `Erreur de fichier : Le fichier fichier_inexistant.png n'existe pas.`

---

## **Sortie**
- Si l'exécution est réussie, le script affiche un message :
  ```plaintext
  Nombre généré : 12345678901234567890
  ```
- En cas d'erreur (fichier introuvable, format non valide), le script affiche un message descriptif.

---

## **Code source**
```python
from PIL import Image
import hashlib
import os
import argparse

# Voir le code complet dans le fichier principal
```

---

## **Avantages dans la cybersécurité**

### **1. Sources d'entropie uniques**
En cybersécurité, l'entropie est essentielle pour générer des valeurs aléatoires ou imprévisibles. Ce script exploite les propriétés uniques des pixels d'une image pour garantir que :
- Chaque image produit un hachage différent.
- L'entropie est élevée grâce à l'algorithme SHA-256.

### **2. Génération de clés de chiffrement reproductibles**
Exemple :
1. Un utilisateur télécharge une image comme "clé visuelle".
2. Le script génère une clé unique basée sur cette image.
3. Tant que l'image d'origine est disponible, la clé peut être recréée pour déchiffrer des données.

---

### **3. Jetons uniques pour l'authentification**
L'entropie des pixels peut être utilisée pour générer des jetons d'accès ou d'authentification temporaires.

#### Exemple :
- Un système utilise une image comme entrée pour générer des jetons d'accès uniques, garantissant qu'un jeton ne peut pas être deviné.

---

Avec ce script, vous avez un outil flexible, sécurisé et facile à utiliser pour tirer parti des images comme sources d'entropie en cybersécurité. 😊
