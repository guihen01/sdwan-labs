# 🖥️ SD-WAN Lab — Simulation sur Eve-NG

Ce lab décrit la **configuration et l’observation d’un environnement SD-WAN** simulé sur la plateforme **Eve-NG**, avec des équipements vEdge et cEdge, et l’utilisation du GUI de **vManage** pour la supervision.

---

## 🧪 Environnement du lab

- **Plateforme de simulation** : Eve-NG
- **Hôte** : Laptop avec 64 Go de RAM
- **Virtualisation** : VMware Workstation Pro v16
- **VM Eve-NG** : taille configurable selon les images SD-WAN
- **Images et ressources SD-WAN utilisées** :
  - vManage v20.7.1 (24 Go RAM)
  - vBond v20.7.1 (2 Go RAM)
  - vSmart v20.7.1 (1 Go RAM)
  - vEdges v20.7.1 (1 Go RAM)
  - c8000v v17.06 (4 Go RAM — recommandé 8 Go pour de meilleures performances)

---

## 🗺️ Topologie et équipements

- **vEdge-2** : observé pour tests BFD
- **vEdge-7** : vEdge classique
- **vEdge-8** : cEdge Cisco c8000v
- **vManage GUI** : supervision globale et vue d’ensemble

---


## ✅ Objectifs et validation

- Simuler un **environnement SD-WAN complet** avec vEdges et cEdges
- Vérifier :
  - la connectivité **control plane** via OMP
  - l’état des **sessions BFD**
  - la visibilité des équipements sur le **GUI vManage**
- Comprendre la différence de comportement et de performance entre :
  - **vEdge** (léger)
  - **cEdge / c8000v** (plus lourd, nécessite plus de RAM)

---

## 🏷️ Mots-clés

`Cisco SD-WAN` · `vEdge` · `cEdge` · `c8000v` · `Eve-NG` · `vManage` · `vSmart` · `vBond` · `BFD` · `OMP` · `Control Plane


