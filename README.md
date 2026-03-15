# 📡 TMA.24063 — Traitement et Modélisation des Signaux

[![Language](https://img.shields.io/badge/Language-Python-blue.svg)](https://github.com/mami572/TMA.24063)
[![Notebook](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://github.com/mami572/TMA.24063)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Active-brightgreen.svg)](https://github.com/mami572/TMA.24063)

Un projet académique complet regroupant les TDs, TPs et le mini-projet du module **TMA (Traitement et Modélisation des Signaux)**. Ce repository couvre l'analyse, le filtrage, et la modélisation de signaux numériques en Python.

---

## 📋 Table des matières

- [🎯 Objectifs](#-objectifs)
- [📚 Contenu du projet](#-contenu-du-projet)
- [🚀 Installation et utilisation](#-installation-et-utilisation)
- [📖 Documentation des TPs](#-documentation-des-tps)
- [🔬 Mini Projet](#-mini-projet)
- [📊 Outils et bibliothèques](#-outils-et-bibliothèques)
- [🤝 Contribution](#-contribution)
- [📄 Licence](#-licence)

---

## 🎯 Objectifs

Ce projet vise à :

- ✅ Analyser et représenter des signaux temporels et fréquentiels
- ✅ Appliquer les techniques de filtrage numérique
- ✅ Comprendre les phénomènes d'aliasing et de quantification
- ✅ Maîtriser l'analyse spectrale via la Transformée de Fourier (FFT)
- ✅ Utiliser Python et Jupyter Notebook pour le traitement du signal

---

## 📚 Contenu du projet

```
TMA.24063/
├── TMA/
│   ├── TDs/              # Travaux dirigés (PDF)
│   ├── TPs/              # Travaux pratiques (Python / Jupyter)
│   │   ├── TP1/          # Analyse de signaux
│   │   ├── TP2/          # Filtrage et analyse spectrale
│   │   └── TP3/          # Aliasing et quantification
│   └── Mini_Projet/      # Projet principal (Jupyter Notebook)
└── README.md
```

---

## 🚀 Installation et utilisation

### Prérequis

- Python 3.8+
- Jupyter Notebook ou JupyterLab
- pip (gestionnaire de paquets Python)

### Installation

```bash
# Cloner le repository
git clone https://github.com/mami572/TMA.24063.git
cd TMA.24063

# Installer les dépendances
pip install numpy scipy matplotlib jupyter

# Lancer Jupyter Notebook
jupyter notebook
```

### Lancer un TP

```bash
cd TMA/TPs/TP1
jupyter notebook TP1_analyse_signaux.ipynb
```

---

## 📖 Documentation des TPs

### 🔷 TP1 — Analyse de signaux

Étude des signaux de base (sinusoïdaux, carrés, triangulaires) dans le domaine temporel.

**Concepts clés :**
- Génération de signaux avec `numpy`
- Représentation temporelle avec `matplotlib`
- Calcul d'amplitude, fréquence et période

```python
import numpy as np
import matplotlib.pyplot as plt

fe = 1000          # Fréquence d'échantillonnage (Hz)
f0 = 10            # Fréquence du signal (Hz)
t = np.arange(0, 1, 1/fe)
x = np.sin(2 * np.pi * f0 * t)

plt.plot(t, x)
plt.title("Signal sinusoïdal")
plt.xlabel("Temps (s)")
plt.ylabel("Amplitude")
plt.show()
```

---

### 🔷 TP2 — Filtrage et analyse spectrale

Application de filtres numériques et analyse du spectre fréquentiel par FFT.

**Concepts clés :**
- Transformée de Fourier Rapide (FFT)
- Filtres passe-bas, passe-haut, passe-bande
- Réponse en fréquence d'un filtre

```python
from scipy.signal import butter, filtfilt
import numpy as np

def filtre_passe_bas(signal, fc, fe):
    """Applique un filtre passe-bas Butterworth"""
    b, a = butter(4, fc / (fe / 2), btype='low')
    return filtfilt(b, a, signal)
```

**Fonctionnalités :**
| Fonction | Description |
|----------|-------------|
| `fft(signal)` | Calcul du spectre de fréquence |
| `butter()` | Conception d'un filtre Butterworth |
| `filtfilt()` | Filtrage sans déphasage |

---

### 🔷 TP3 — Aliasing et quantification

Étude des effets de sous-échantillonnage et de la quantification numérique.

**Concepts clés :**
- Théorème de Shannon-Nyquist : `fe ≥ 2 × f_max`
- Repliement spectral (aliasing)
- Quantification sur N bits : `2^N` niveaux
- Rapport Signal sur Bruit de Quantification (RSBQ)

```python
# Démonstration de l'aliasing
f_signal = 100  # Hz
fe_ok = 500     # Respect de Shannon : fe > 2 * f_signal
fe_alias = 80   # Violation : fe < 2 * f_signal → aliasing !
```

---

## 🔬 Mini Projet

Le mini-projet est réalisé entièrement en **Jupyter Notebook** et rassemble les concepts vus en TD/TP dans une étude de cas complète.

**Thématiques abordées :**
- Acquisition et prétraitement d'un signal réel
- Analyse spectrale avancée
- Application d'un filtre adapté au signal
- Interprétation et visualisation des résultats

---

## 📊 Outils et bibliothèques

| Bibliothèque | Usage |
|--------------|-------|
| `numpy` | Calcul numérique, génération de signaux |
| `scipy.signal` | Filtrage, convolution, FFT avancée |
| `matplotlib` | Visualisation temporelle et spectrale |
| `jupyter` | Environnement de travail interactif |

### Complexités des opérations courantes

| Opération | Complexité |
|-----------|------------|
| FFT (N points) | O(N log N) |
| Filtrage FIR (ordre M) | O(N × M) |
| Filtrage IIR (Butterworth) | O(N) |
| Quantification | O(N) |

---

## 🚧 Fonctionnalités à venir

- [ ] Interface interactive avec `ipywidgets`
- [ ] TP4 : Modélisation AR/MA
- [ ] Analyse temps-fréquence (STFT, spectrogramme)
- [ ] Export automatique des rapports en PDF
- [ ] Tests et validation automatisés

---

## 🤝 Contribution

Les contributions sont les bienvenues ! Pour contribuer :

1. 🍴 Fork le projet
2. 🌟 Créer une branche (`git checkout -b feature/nouvelle-analyse`)
3. 💾 Commit vos changements (`git commit -am 'Ajout d'une nouvelle analyse'`)
4. 📤 Push vers la branche (`git push origin feature/nouvelle-analyse`)
5. 🔄 Créer une Pull Request

### Guidelines de contribution

- Documenter les notebooks avec des cellules Markdown claires
- Inclure des visualisations pour chaque résultat
- Respecter les conventions de nommage Python (PEP 8)
- Tester le code avant de soumettre

---

## 📞 Contact

**Auteur** : [mami572](https://github.com/mami572)

- 🔗 GitHub : [@mami572](https://github.com/mami572)

---

## 📄 Licence

Ce projet est sous licence MIT. Voir le fichier [LICENSE](LICENSE) pour plus de détails.

---

## ⭐ Remerciements

Si ce projet vous a été utile pour vos études en traitement du signal, n'hésitez pas à lui donner une étoile ⭐ !

---

<div align="center">
  <b>Fait avec ❤️ pour l'apprentissage du traitement du signal</b>
</div>
