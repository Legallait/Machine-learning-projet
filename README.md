# Teaching Computers to See : classification Cats vs Dogs avec un CNN

Projet ST2AIM, EFREI Paris. Construction, entraînement et évaluation d'un Convolutional Neural Network capable de distinguer des images de chats et de chiens, puis amélioration du modèle avec la data augmentation, le dropout, la batch normalization et le transfer learning.

## Équipe

- Estermann Nicolas
- Hartz Henri
- CESA Matthew-Frédérick
- NGUYEN Constant

## Structure du projet

### Préparation du dataset

Le dataset n'est pas versionné sur GitHub. Avant d'exécuter le notebook, il faut créer un dossier `data/` à la racine du projet et y placer le dossier `cats_and_dogs_filtered`, qui contient les images de chats et de chiens. L'arborescence attendue est la suivante :

    data/
    └── cats_and_dogs_filtered/
        ├── train/
        │   ├── cats/
        │   └── dogs/
        └── validation/
            ├── cats/
            └── dogs/

## Prérequis

- Python 3.13 (3.12 fonctionne aussi)
- Git
- PyCharm, VS Code ou Jupyter

## Installation

### 1. Cloner le repo

```bash
git clone https://github.com/<utilisateur>/Machine-learning-projet.git
cd Machine-learning-projet
```

### 2. Créer et activer l'environnement virtuel

**Windows (PowerShell)**

```powershell
python -m venv .venv
.venv\Scripts\activate
```

Si PowerShell bloque l'activation, lancer une fois :

```powershell
Set-ExecutionPolicy -Scope CurrentUser RemoteSigned
```

**macOS / Linux**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

Une fois activé, `(.venv)` apparaît au début de la ligne du terminal.

### 3. Installer les dépendances

```bash
pip install -r requirements.txt
```

### 4. Configurer nbstripout

nbstripout retire les métadonnées d'exécution du notebook à chaque commit (numéros de cellules, horaires d'exécution) tout en gardant les sorties. Cela évite les diffs inutiles et les conflits Git. La configuration est locale : chaque membre de l'équipe doit la faire une fois.

```bash
nbstripout --install --keep-output
git config filter.nbstripout.extrakeys "cell.metadata.jupyter.is_executing"
```

Vérification :

```bash
nbstripout --status
```

### 5. Sélectionner l'interpréteur dans l'IDE

**PyCharm** : Settings > Project > Python Interpreter > Add Interpreter > Existing, puis sélectionner :

- Windows : `.venv\Scripts\python.exe`
- macOS : `.venv/bin/python`

**VS Code** : `Ctrl+Shift+P` (`Cmd+Shift+P` sur Mac) > Python: Select Interpreter > `.venv`.

## Dataset

Le dataset `cats_and_dogs_filtered` est téléchargé automatiquement dans `data/` à la première exécution du notebook. Il n'est pas versionné sur GitHub.

Téléchargement manuel si besoin : [cats_and_dogs_filtered.zip](https://storage.googleapis.com/mledu-datasets/cats_and_dogs_filtered.zip), à extraire dans `data/` pour obtenir :

```
data/cats_and_dogs_filtered/
├── train/        1000 cats, 1000 dogs
└── validation/   500 cats, 500 dogs
```

Le dossier `train` est découpé en 80 % entraînement (1600 images) et 20 % test (400 images). Le dossier `validation` sert au suivi pendant l'entraînement.

## Utilisation

Ouvrir `main.ipynb` et exécuter les cellules dans l'ordre. L'entraînement sur CPU prend quelques minutes par epoch.

## Résultats

| Modèle | Accuracy | Precision | Recall | F1-score |
|---|---|---|---|---|
| Baseline CNN | | | | |
| Data augmentation | | | | |
| Dropout + Batch Normalization | | | | |
| Transfer learning (MobileNetV2) | | | | |

## Travailler à plusieurs

1. Avant de commencer : `git pull`
2. Une seule personne modifie `main.ipynb` à la fois
3. Après chaque étape : commit avec un message clair, puis `git push`

## Sources

- Dataset : [Google ML Education, cats_and_dogs_filtered](https://storage.googleapis.com/mledu-datasets/cats_and_dogs_filtered.zip)
- [Documentation TensorFlow / Keras](https://www.tensorflow.org/api_docs/python/tf/keras)
- [MobileNetV2, Keras Applications](https://keras.io/api/applications/mobilenet/)
