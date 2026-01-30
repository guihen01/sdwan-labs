# 🧪 SD-WAN Lab — QoS & Central Policy (Cisco SD-WAN)

Ce lab démontre l’application d’une **politique centrale de QoS** dans un environnement **Cisco SD-WAN**, avec **marquage DSCP** du trafic, gérée via **vManage** et propagée par **vSmart** vers les **vEdges**.

L’objectif est de montrer le chemin complet d’une **Central Policy** :
vManage → vSmart → vEdges → vérification terrain (ping + capture Wireshark).

---

## 🧱 Environnement du lab

- **Plateforme de lab** : Eve-NG  
- **Contrôleurs SD-WAN** :
  - vManage : 20.7.1
  - vSmart  : 20.7.1
  - vBond   : 20.7.1
- **Routeurs** :
  - vEdges  : 20.7.1  
- **Remarque** :  
  Tous les vEdges ne sont **pas démarrés** pour ce lab (topologie réduite).

---

## 🧩 Préambule

- vManage et vSmart sont configurés en **mode vManage (template-based)**  
- Les équipements **ne sont plus gérés en CLI direct**
- Les templates utilisés sont :
  - **Templates basés sur CLI**
  - Créés et attachés depuis vManage

---

## 🎯 Objectif du lab

- Créer une **Central Policy** de QoS sur vManage
- Appliquer la policy :
  - au **site 3**
  - au **VPN 5**
- Vérifier :
  - la propagation via **vSmart**
  - l’application effective sur les **vEdges**
  - le **marquage DSCP** du trafic utilisateur

---

## 🛠️ Étape 1 — Création de la Central Policy (vManage)

- La **Central Policy** est définie sur **vManage**
- Portée de la policy :
  - **Site ID : 3**
  - **VPN : 5**
- Le VPN 5 est **à l’intérieur du périmètre du site 3**

---

## ▶️ Étape 2 — Activation de la policy

- Une fois la policy créée :
  - elle est **activée dans vManage**
  - elle est automatiquement **poussée vers vSmart**

vSmart devient alors responsable de l’application dynamique de la policy.

---

## 🔁 Étape 3 — Application par vSmart

- vSmart applique la policy :
  - aux **vEdges du site 3**
  - sur le **VPN 5**
- Sur **vEdge-7** (site 3), on peut constater que :
  - la policy QoS est bien reçue
  - la configuration est injectée dynamiquement par vSmart

*(Configuration visible côté vSmart / vEdge)*

---

## 🧪 Étape 4 — Tests & validation

### 🔹 Étape 4.1 — Test de connectivité

- Depuis un **VPC dans le VPN 5**
- Ping vers :  

