# Projet Master 1 Informatique : Analyse de Fraude Bancaire

## "Outils libres pour le développement logiciel"


---

### 1. Introduction au Projet

Ce projet a pour objectif d'appliquer un ensemble d'outils libres de développement logiciel pour l'analyse de données, en se concentrant sur un cas d'étude dans le domaine de la finance : la détection de fraude par carte bancaire. Il vise à démontrer la maîtrise des compétences en gestion de version (Git/GitHub), manipulation de données (Python/Pandas/Jupyter), intégration de base de données (PostgreSQL), et analyse exploratoire de données.

### 2. Dataset Utilisé

**Nom :** Credit Card Fraud Detection
**Source :** [Kaggle](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)
**Description :** Ce dataset contient des transactions par carte de crédit effectuées par des citoyens européens en septembre 2013. Il comprend 284 807 transactions, dont 492 sont frauduleuses. Les caractéristiques `V1` à `V28` sont le résultat d'une transformation PCA (Analyse en Composantes Principales) pour des raisons de confidentialité, tandis que `Time` (secondes écoulées depuis la première transaction) et `Amount` (montant de la transaction) sont les seules caractéristiques originales non transformées. La colonne `Class` indique la fraude (1) ou la non-fraude (0).

### 3. Outils et Technologies Utilisés

*   **Gestion de Version :** Git / GitHub
*   **Environnement de Développement :** Jupyter Notebook (lancé dans WSL/Ubuntu)
*   **Langage de Programmation :** Python 3
*   **Bibliothèques Python :**
    *   `pandas` : Manipulation et analyse de données.
    *   `numpy` : Opérations numériques.
    *   `matplotlib` & `seaborn` : Visualisation de données.
    *   `scikit-learn` : Pour les outils de pré-traitement (StandardScaler).
    *   `psycopg2` : Pilote pour la connexion à PostgreSQL.
    *   `SQLAlchemy` : Couche d'abstraction pour la base de données, utilisée par Pandas.
*   **Base de Données :** PostgreSQL (installé dans WSL/Ubuntu)

### 4. Reproduction du Projet (Instructions pour l'Enseignant)

Pour reproduire ce projet localement, suivez les étapes suivantes :

1.  **Cloner le Dépôt Git :**
    Ouvrez un terminal (WSL/Ubuntu recommandé) et exécutez :
    ```bash
    git clone https://github.com/salutos93/finance.git
    cd finance
    ```

2.  **Configuration de l'Environnement Python (WSL/Ubuntu) :**
    *   **Créer et Activer l'Environnement Virtuel :**
        ```bash
        python3 -m venv venv
        source venv/bin/activate
        ```
    *   **Installer les Dépendances Python :**
        ```bash
        pip install jupyter pandas numpy matplotlib seaborn psycopg2-binary scikit-learn sqlalchemy
        ```

3.  **Installation et Configuration de PostgreSQL (WSL/Ubuntu) :**
    *   **Installer PostgreSQL :**
        ```bash
        sudo apt update
        sudo apt install -y postgresql postgresql-contrib python3-venv
        sudo systemctl start postgresql # Démarrer le service si nécessaire
        ```
    *   **Créer l'Utilisateur et la Base de Données :**
        Connectez-vous à `psql` en tant qu'administrateur et créez les identifiants utilisés dans le notebook (remplacez par les vôtres si vous n'avez pas utilisé `monprojetuser`/`mdp_projet_finance`/`fraude_db`) :
        ```bash
        sudo -u postgres psql
        # Dans psql :
        CREATE USER fraude WITH PASSWORD 'mdp_projet_fraude';
        CREATE DATABASE fraude_db OWNER fraude;
        GRANT ALL PRIVILEGES ON DATABASE fraude_db TO monprojetuser;
        \q
        ```

4.  **Téléchargement du Dataset :**
    Le fichier `creditcard.csv` n'est pas inclus dans le dépôt Git car il dépasse la limite de taille de GitHub. Il doit être téléchargé manuellement :
    *   Allez sur la page Kaggle du dataset : [https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)
    *   Cliquez sur "Download".
    *   Dézippez le fichier `creditcardfraud.zip`.
    *   **Placez le fichier `creditcard.csv` directement dans le répertoire racine du projet** (`finance/`) que vous venez de cloner.

5.  **Lancer Jupyter Notebook et Exécuter l'Analyse :**
    *   Assurez-vous que l'environnement virtuel est actif (`(venv)` dans le terminal).
    *   Lancez Jupyter : `jupyter notebook`
    *   Ouvrez le notebook `Exploration_Fraude.ipynb`.
    *   **Redémarrez le kernel** (obligatoire pour utiliser les bonnes dépendances).
    *   Exécutez toutes les cellules du notebook séquentiellement. Le notebook contient le code pour charger les données, les préparer, les insérer dans PostgreSQL, et réaliser l'analyse exploratoire et les visualisations.

### 5. Structure du Dépôt

*   `Exploration_Fraude.ipynb` : Le notebook principal contenant l'intégralité du code et des analyses.
*   `.gitignore` : Fichier de configuration Git pour ignorer les dossiers `venv/`, `.ipynb_checkpoints/`, et les fichiers `creditcard.csv`, `creditcardfraud.zip`.
*   `README.md` : Ce fichier de documentation.

---
