# 🌐 SD-WAN Lab — Direct Internet Access (DIA) avec cEdge (Cisco c8000v)

Ce lab démontre la mise en œuvre du **Direct Internet Access (DIA)** dans un environnement **Cisco SD-WAN**, afin de fournir un **accès Internet direct aux utilisateurs invités**, en utilisant un **cEdge Cisco c8000v** et une configuration **NAT DIA basée sur VRF**.

Contrairement au lab précédent basé sur vEdges, celui-ci met en évidence les **différences de configuration entre vEdge et cEdge**.

---

## 🧪 Environnement du lab

- **Plateforme de simulation** : Eve-NG
- **Contrôleurs SD-WAN** :
  - vManage : 20.7.1 (24 Go RAM)
  - vSmart  : 20.7.1 (2 Go RAM)
  - vBond   : 20.7.1 (1 Go RAM)
- **Routeurs SD-WAN** :
  - vEdges : 20.7.1 (1 Go RAM)
  - cEdges : Cisco c8000v — **v17.06.03a** (2 Go RAM)

---

## 📌 Notes importantes

- Le lab est basé sur un **mélange de vEdges et cEdges**
- Les **cEdges (Cisco c8000v)** utilisent :
  - un **jeu de commandes IOS-XE**
  - une **approche différente** de celle des vEdges
- Dans ce lab :
  - le cEdge est nommé **Vedge-8**
  - seul le **c8000v est activé** côté utilisateurs
- Une autre méthode DIA existe avec les cEdges :
  - via des **Data Policies sur vSmart**
  - qui fera l’objet d’un **lab ultérieur**

---

## 🗺️ Topologie (vue partielle)

- Le schéma représente uniquement la **partie haute du plan**
- Le routeur **ISP-R** :
  - fournit l’accès Internet
  - est connecté via **interface e1/3**
  - est relié au **cloud WAN (cloud1-NAT)**
- Les routeurs **ISP-R** et **MPLS-R** :
  - symbolisent les clouds Internet / MPLS
  - représentent, en conditions réelles, un ensemble d’équipements WAN

---

## 🎯 Objectif du lab

- Fournir un **accès Internet direct** aux utilisateurs du **VRF 9**
- Implémenter le **DIA via NAT sur cEdge**
- Valider :
  - la route par défaut NAT DIA
  - la connectivité Internet
  - la visibilité OMP/TLOC

---

## ⚙️ Configuration sur cEdge (Vedge-8)

### 🔹 Vérification des VRF

Les VRF utilisateurs doivent être **préconfigurés globalement**.


Résultat :
- résolution DNS fonctionnelle
- accès Internet validé


➡️ Les utilisateurs du **VRF 9** ont accès à Internet  
➡️ La route statique **NAT DIA fonctionne correctement**

---

## 🔄 Fonctionnement du flux DIA

1. Le trafic est généré dans le **VRF 9**
2. Les paquets entrent via **Gi3**
3. La route par défaut **NAT DIA** est utilisée
4. Le trafic est NATé sur :
   - **GigabitEthernet1**
5. Les paquets sont envoyés vers Internet via **ISP-R**

---

## 📡 Commandes SD-WAN complémentaires

### 🔹 TLOCs sur cEdge

show sdwan omp tlocs

Résultat :
- deux TLOCs visibles sur Vedge-8 :
  - `3.3.3.3 mpls ipsec`
  - `3.3.3.3 biz-internet ipsec`

---

### 🔹 Sessions BFD

show sdwan bfd sessions
Résultat :
- aucune session BFD
- comportement attendu :
  - les autres vEdges ne sont pas activés dans ce lab

---

## 🧠 Vérifications côté vSmart

show omp tlocs | tab
- visibilité des TLOCs annoncés par le cEdge
- validation du contrôle-plane


## ✅ Conclusion

Ce lab valide :
- la mise en œuvre du **DIA avec cEdge (c8000v)**
- l’utilisation du **NAT DIA basé sur VRF**
- les différences clés entre :
  - **vEdge**
  - **cEdge (IOS-XE)**
- une architecture réaliste pour :
  - accès Internet local
  - utilisateurs invités

---

## 🏷️ Mots-clés

`Cisco SD-WAN` · `DIA` · `cEdge` · `c8000v` · `IOS-XE` · `NAT DIA` · `VRF` · `Eve-NG`
