# Application de la programmation en nombres entiers aux cryptosystèmes post-quantiques basés sur les réseaux

Ce dépot correspond à l'ensemble du travail réalisé lors d'un projet d'initialisation à la recherche réalisé à l'été 2026 à l'UdeM. Ce projet avait comme sujet d'analyser les liens entre la programmation en nombres entiers et les cryptosystèmes basés sur les réseaux euclidiens. 

Plus particulièrement, le projet s'est concentré sur la réalisation d'une attaque du problème cryptographique **Learning With Errors**, que l'on abbréviera par souci de lisibilité à **LWE**. 

Le dépot contient:
1. Les rapports de recherche ayant découlés de ce travail. 
2. Le code source du solveur implémenté. 

## Rapports de recherche

Les deux documents *pdf* de ce travail sont très similaires, mais ont deux vocations différentes. 

- **[Rapport de recherche (PDF)](./2026_LWE_IP_Lessnick.pdf)**  
  Document remis au comité d'évaluation du département d'informatique et de recherche opérationnel dans le cadre du projet. C'est le document qui **devrait être consulté par 99% des visiteurs de ce projet**. Il contient l'entièreté de la démarche mathématique et présente les résultats expérimentaux obtenus, tout en explicitant les quelques prérequis mathématiques nécessaire à la compréhension du travail. 

- **[Rapport étendu et revue de littérature (PDF)](./2026_RevueDetaillee_PQC_IP_Lessnick.pdf)**  
  Document plus exhaustif débutant par une revue de littérature de 30 pages agissant à titre d'introduction à la cryptographie pour un étudiant au baccalauréat n'y étant pas initié. C'est un document tant pour les curieux que pour ceux cherchant à s'introduire au contexte global dans lequel s'incrit la cryptographie post-quantique.


## Structure du dépôt

```text
solveur_ip_lwe/
├── src/                                    # Code source des solveurs et benchmarks
├── 2026_LWE_IP_Lessnick.pdf                # Rapport de recherche
├── 2026_RevueDetaillee_PQC_IP_Lessnick.pdf # Rapport étendu / revue de littérature
└── requirements.txt                        # Dépendances Python
```

## Installation et configuration

### Prérequis
* Python 3.10 ou supérieur 
* Une licence active pour le solveur **Gurobi** (licence académique WLS ou Named-User).
* Système Linux ou environnement WSL (ou équivalent). Est nécessaire pour l'utilisation de la librairie FPyLLL, mais n'est pas essentielle si le solveur choisi n'est pas celui utilisant l'algorithme LLL.

### 1. Cloner le dépôt
```bash
git clone [https://github.com/alexlesss/solveur_ip_lwe.git](https://github.com/alexlesss/solveur_ip_lwe.git)
cd solveur_ip_lwe
```

### 2. Créer et activer l'environnement virtuel
```bash
python3 -m venv env_lwe
source env_lwe/bin/activate
```

### 3. Installer les dépendances
```bash
pip install -r requirements.txt
```

---

## Utilisation

Les scripts s'exécutent depuis le dossier source :

```bash
cd src
```
### Test de validation rapide
Il est possible de s'assurer du bon fonctionnement du solveur via:
```bash
python test_manuel.py
```

### Exécution d'un banc d'essai
Il est possible de démarrer la résolution d'un groupe d'instances via:
```bash
python benchmark.py
```
Les résultats de cette dernière seront alors affichés dans un fichier *csv* qui sera généré.

La configuration des tests s'effectue directement dans `src/benchmark.py`. Il est possible d'y ajuster :
* Le générateur de paramètres et les dimensions d'instances (n, m, q, t).
* Le générateur d'instances selon la distribution que l'on utilise pour t.
* La variante du solveur de PQNE que l'on veut utiliser. 
* Le nombre de répétitions par instance ainsi que le temps d'arrêt précoce.

Une automatisation de la personnalisation est à venir, car elle est pour l'instant assez ardue sans expérience préablable

## Auteur

* **Alexis Lessnick** — Étudiant à l'Université de Montréal (DIRO)

