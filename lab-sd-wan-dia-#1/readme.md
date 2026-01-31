# 🌐 SD-WAN Lab — Direct Internet Access (DIA) pour utilisateurs invités

Ce lab démontre la mise en place du **Direct Internet Access (DIA)** dans un environnement **Cisco SD-WAN** basé sur des **vEdges**, afin de fournir un accès Internet direct aux **utilisateurs du VPN 5 (guest users)**.

Le trafic utilisateur est **NATé localement** et redirigé vers Internet via le **VPN 0**, sans passer par le backbone SD-WAN.

---

## 🧪 Environnement du lab

- **Plateforme de simulation** : Eve-NG
- **Contrôleurs SD-WAN** :
  - vManage : 20.7.1 (24 Go RAM)
  - vSmart  : 20.7.1 (2 Go RAM)
  - vBond   : 20.7.1 (1 Go RAM)
- **Routeurs** :
  - vEdges  : 20.7.1 (1 Go RAM)
- **Accès Internet** :
  - Routeur **ISP-R**
  - Sortie Internet via **interface e1/3**

---

## 📌 Notes importantes

- Ce lab est basé **exclusivement sur des vEdges**
- Les **cEdges (Cisco c8000v)** utilisent un jeu de commandes différent  
  → une autre approche serait nécessaire
- La configuration DIA avec **cEdges** fera l’objet d’un **lab séparé**
- Une autre méthode DIA existe avec :
  - **Data Policies via vSmart**
  → également prévue pour un futur lab
- La topologie présentée est **partielle**, pour des raisons de lisibilité

---

## 🗺️ Topologie (vue partielle)

- Point de départ utilisateurs : **vEdge-7**
- Accès Internet fourni via :
  - VPN 0
  - Interface WAN connectée au routeur ISP-R

---

## 🎯 Objectif du lab

- Fournir un **accès Internet direct** aux utilisateurs du **VPN 5**
- Utiliser :
  - une **route statique par défaut**
  - du **NAT local sur le vEdge**
- Valider le fonctionnement via :
  - table de routage
  - tests de connectivité (ping)

---

## ⚙️ Configuration

### 🔹 Configuration sur vEdge-7 — VPN 0 (Internet)

Sur l’interface connectée à l’ISP :


