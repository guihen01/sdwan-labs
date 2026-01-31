# 🌐 SD-WAN Lab — Direct Internet Access (DIA) via Vsmart Policy

Ce lab démontre la mise en œuvre du **Direct Internet Access (DIA)** pour des utilisateurs invités dans un environnement **Cisco SD-WAN**, en utilisant un **cEdge Cisco c8000v** et des **Data-Policies définies sur Vsmart**.  

Contrairement au lab précédent (DIA NAT classique sur cEdge), ici le contrôle est centralisé via **policies Vsmart** qui sont poussées dynamiquement vers le cEdge.

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
- **Routeur ISP** : ISP-R, connectivité Internet via **interface e1/3**
- **cEdge utilisé pour le lab** : **Vedge-8**
- **VRF utilisateur activé** : VRF 9 (interface Gi3)

---

## 📌 Notes importantes

- Les **cEdges (c8000v)** utilisent un **jeu de commandes IOS-XE** différent des vEdges
- La méthode DIA via **Vsmart policy** permet :
  - le contrôle centralisé du NAT
  - la définition d’adresses IP ou de plages autorisées
- Seules certaines IP du VRF 9 (10.1.9.1 et 10.1.9.2) sont autorisées à accéder à Internet
- Les adresses non incluses dans la policy sont bloquées (**blackhole**)

---

## 🗺️ Topologie (vue partielle)

- Partie haute du plan : routeurs **ISP-R**, **MPLS-R**
- Partie basse : **cEdge Vedge-8**, autres vEdges
- Les routeurs ISP-R et MPLS-R sont symbolisés par des **nuages Internet / MPLS**
- Le Vedge-8 est connecté au WAN via Gi1 et au VRF utilisateur via Gi3

---

## 🔄 Fonctionnement DIA via Vsmart Policy

1. Trafic généré par VRF 9 (utilisateurs)
2. Policy Vsmart appliquée automatiquement sur Vedge-8
3. Seules les adresses IP autorisées dans la prefix-list sont redirigées vers Internet
4. Trafic NATé sur Gi1 et envoyé vers ISP-R
5. IP non listées : **blackhole**, pas de sortie Internet


## ✅ Conclusion

- Mise en place du **DIA basé sur Vsmart policy**
- Contrôle centralisé et ciblé sur certaines adresses IP du VRF
- Validation des compteurs et des chemins NAT
- Comportement correct des adresses autorisées et filtrage des non-autorisées

---

## 🏷️ Mots-clés

`Cisco SD-WAN` · `DIA` · `cEdge` · `c8000v` · `Vsmart policy` · `Data-policy` · `VRF 9` · `Eve-NG` · `NAT DIA



