# 📡 NetScope — Labo de détection & analyse réseau

<p align="left">
  <img src="https://img.shields.io/badge/Python-3.11+-0D0D0D?style=flat-square&logo=python&logoColor=A855F7" alt="Python" />
  <img src="https://img.shields.io/badge/Nmap-0D0D0D?style=flat-square&logo=linux&logoColor=A855F7" alt="Nmap" />
  <img src="https://img.shields.io/badge/R-Analyse-0D0D0D?style=flat-square&logo=r&logoColor=A855F7" alt="R" />
  <img src="https://img.shields.io/badge/Wireshark-0D0D0D?style=flat-square&logo=wireshark&logoColor=A855F7" alt="Wireshark" />
  <img src="https://img.shields.io/badge/Statut-Planifié-8A2BE2?style=flat-square" alt="Statut" />
</p>

Mini laboratoire de supervision réseau monté sous **VirtualBox** : découvrir le réseau,
surveiller les connexions, détecter les comportements suspects et produire un rapport lisible.
C'est le quotidien d'un **analyste SOC**, condensé dans un projet reproductible.

## ✨ Fonctionnalités

- [ ] Cartographie automatique : appareils, ports ouverts, services actifs
- [ ] Surveillance en temps réel : alerte à chaque nouvel appareil
- [ ] Analyse de trafic : identification des connexions suspectes
- [ ] Analyse statistique des logs en R : tendances et graphiques
- [ ] Génération automatique d'un rapport de synthèse (Markdown / PDF)
- [ ] Tableau de bord simple (CLI ou web)

## 🧱 Pipeline

```text
 Découverte            Surveillance          Analyse              Restitution
┌──────────┐   ┌──────────────────┐   ┌──────────────┐   ┌────────────────┐
│  Nmap    │ → │  Watch / captures │ → │  Python + R   │ → │  Rapport + graph │
│  scan    │   │  (Wireshark/tcpdump)│  │  statistiques │   │  Markdown / PDF  │
└──────────┘   └──────────────────┘   └──────────────┘   └────────────────┘
```

## 🗂️ Structure

```text
netscope/
├── src/
│   ├── discovery.py       # Scan Nmap (hôtes, ports, services)
│   ├── monitor.py         # Surveillance et alertes
│   ├── analyze.py         # Traitement des logs
│   └── report.py          # Génération du rapport
├── r/
│   └── stats.R            # Analyse statistique et graphiques
├── logs/                  # Journaux horodatés
├── reports/               # Rapports générés
├── lab/                   # Config VirtualBox + schéma réseau
└── tests/
```

## 🚀 Installation

```bash
git clone https://github.com/MolkaHassine/netscope.git
cd netscope
python -m venv .venv
# Windows : .venv\Scripts\activate
source .venv/bin/activate
pip install -r requirements.txt
sudo apt install nmap r-base    # ou équivalent
```

## ▶️ Utilisation

```bash
python -m src.discovery --range 192.168.56.0/24
python -m src.monitor --interface eth0
python -m src.analyze --logs logs/
python -m src.report --output reports/rapport.md
Rscript r/stats.R
```

## 📊 Résultats attendus

- Nombre d'hôtes découverts et évolution dans le temps
- Top des ports/services exposés
- Détection de nouveaux équipements (avec horodatage)
- Graphiques de fréquence des connexions par plage horaire

## ⚠️ Éthique & légal

Ce projet est destiné **exclusivement** à un laboratoire personnel isolé
(réseau host-only VirtualBox). Ne scannez jamais un réseau dont vous n'êtes pas
propriétaire ou administrateur. Documentez toujours votre périmètre.

## 🗺️ Roadmap

- [ ] Isoler le lab (host-only) + documentation du schéma
- [ ] Script de découverte + export JSON
- [ ] Surveillance des nouveaux hôtes (diff entre scans)
- [ ] Analyse R + graphiques
- [ ] Rapport final + démo vidéo/GIF

## 📬 Contact

Molka Hassine — [molka.hassine@polytechnicien.tn](mailto:molka.hassine@polytechnicien.tn)

## 📄 Licence

MIT — voir [LICENSE](../../LICENSE).
