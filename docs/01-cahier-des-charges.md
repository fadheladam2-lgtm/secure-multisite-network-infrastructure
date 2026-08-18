# Cahier des charges
## Infrastructure réseau multisite sécurisée et hautement disponible

---

## 1. Contexte

L'entreprise dispose d'un siège et d'une agence distante.

L'objectif du projet est de concevoir et simuler une infrastructure
réseau permettant aux différents services de l'entreprise de
communiquer de manière sécurisée tout en assurant la disponibilité
et la continuité du réseau.

L'infrastructure doit également permettre une évolution future
vers une architecture réelle intégrant des solutions de sécurité,
de VPN et de supervision.

---

## 2. Objectifs du projet

Le projet a pour objectifs de :

- Concevoir une architecture réseau d'entreprise multisite
- Segmenter les utilisateurs à l'aide de VLAN
- Mettre en place le routage inter-VLAN
- Déployer un protocole de routage dynamique OSPF
- Mettre en place une architecture réseau redondante
- Assurer la haute disponibilité des passerelles
- Sécuriser les accès aux équipements
- Contrôler les communications entre les différents services
- Interconnecter le siège et l'agence
- Tester la résistance de l'infrastructure aux pannes
- Documenter l'ensemble de l'architecture

---

## 3. Organisation de l'entreprise

### 3.1 Siège

Le siège regroupe les services suivants :

| Service | VLAN | Nombre d'utilisateurs |
|---|---:|---:|
| Administration | 10 | 10 |
| Employés | 20 | 60 |
| IT | 30 | 15 |
| RH | 40 | 10 |
| Direction | 50 | 5 |
| Management | 99 | Équipements |
| **Total** | | **100** |

### 3.2 Agence distante

L'agence dispose des services suivants :

| Service | VLAN |
|---|---:|
| Administration | 10 |
| RH | 40 |
| Management | 99 |

---

## 4. Architecture réseau

L'architecture sera organisée autour de plusieurs niveaux :

### Cœur de réseau

Deux switches Layer 3 seront utilisés afin d'assurer
la redondance du cœur réseau.

### Couche d'accès

Deux switches d'accès permettront de connecter les postes
utilisateurs aux différents VLAN.

### Interconnexion des sites

Le siège et l'agence seront reliés par une infrastructure WAN.

OSPF sera utilisé pour le routage dynamique.

---

## 5. Segmentation réseau

### Siège

| VLAN | Nom | Fonction |
|---:|---|---|
| 10 | ADMIN | Administration |
| 20 | EMPLOYES | Utilisateurs |
| 30 | IT | Équipe informatique |
| 40 | RH | Ressources humaines |
| 50 | DIRECTION | Direction |
| 99 | MANAGEMENT | Administration réseau |

### Agence

| VLAN | Nom | Fonction |
|---:|---|---|
| 10 | ADMIN | Administration |
| 40 | RH | Ressources humaines |
| 99 | MANAGEMENT | Administration réseau |

La segmentation permet de limiter les communications directes
entre les différents services et de contrôler les flux à l'aide
de mécanismes de filtrage.

---

## 6. Routage

Le routage inter-VLAN sera assuré par les switches Layer 3.

Le protocole OSPF sera utilisé pour :

- Échanger dynamiquement les routes
- Permettre la communication entre les différents réseaux
- Faciliter l'évolution de l'infrastructure
- Fournir plusieurs chemins lorsque cela est possible
- Améliorer la résilience du réseau

---

## 7. Haute disponibilité

L'infrastructure devra limiter les points uniques de défaillance.

Les mécanismes suivants seront étudiés :

- Deux switches Layer 3
- Deux switches d'accès
- Liens redondants
- EtherChannel / LACP
- Spanning Tree Protocol
- HSRP
- Plusieurs chemins de routage avec OSPF

L'objectif est de permettre au réseau de continuer à fonctionner
en cas de panne d'un lien ou d'un équipement critique.

---

## 8. Sécurité

Les mesures de sécurité suivantes seront mises en œuvre :

### Sécurisation des équipements

- SSH
- Authentification
- Mots de passe chiffrés
- Désactivation des ports inutilisés
- Port Security
- BPDU Guard

### Contrôle des flux

Des ACL seront utilisées afin de contrôler les communications
entre les différents VLAN.

Le principe du moindre privilège sera appliqué autant que possible.

### Management

Le VLAN 99 sera réservé à l'administration des équipements réseau.

Les postes utilisateurs ne devront pas pouvoir accéder directement
aux interfaces de management.

---

## 9. Services réseau

Les services suivants seront étudiés ou simulés :

- DHCP
- DNS
- NTP
- NAT/PAT
- SSH

---

## 10. Environnement de simulation

La maquette principale sera réalisée avec :

**Cisco Packet Tracer**

Cette plateforme permettra de simuler notamment :

- VLAN
- Trunk
- Routage inter-VLAN
- OSPF
- STP
- EtherChannel
- HSRP
- ACL
- DHCP
- NAT/PAT
- SSH
- Sécurité des ports

---

## 11. Évolution vers une infrastructure réelle

Certaines fonctionnalités pourront être étudiées dans une
évolution future du projet.

Cette évolution pourra notamment intégrer :

- pfSense
- OpenVPN
- DMZ
- Reverse Proxy
- Nginx
- Supervision
- Centralisation des journaux

Ces composants ne font pas partie de la maquette Packet Tracer
principale et seront considérés comme des extensions vers une
infrastructure virtuelle ou réelle.

---

## 12. Tests et validation

L'infrastructure sera validée par plusieurs séries de tests.

### VLAN

- Vérification de l'appartenance des ports
- Vérification des trunks
- Vérification de l'isolation des VLAN

### Routage

- Ping inter-VLAN
- Vérification des routes
- Vérification des voisins OSPF

### Haute disponibilité

- Test de coupure d'un lien
- Test de coupure d'un switch
- Test du fonctionnement HSRP
- Vérification d'EtherChannel
- Vérification de STP

### Sécurité

- Tests des ACL
- Tests de Port Security
- Vérification de SSH
- Vérification du VLAN Management

### WAN

- Communication entre le siège et l'agence
- Vérification des routes OSPF
- Test de la résilience des chemins

---

## 13. Livrables

Le projet devra produire :

- Cahier des charges
- Schéma logique
- Schéma physique
- Plan VLAN
- Plan d'adressage IP
- Plan de routage
- Configurations des équipements
- Fichier Packet Tracer
- Procédures de tests
- Résultats des tests
- Documentation technique

---

## 14. Critères de réussite

Le projet sera considéré comme fonctionnel lorsque :

- Les VLAN sont correctement configurés
- Les trunks fonctionnent
- Le routage inter-VLAN fonctionne
- OSPF établit correctement ses voisinages
- Le siège communique avec l'agence
- HSRP assure la redondance de passerelle
- EtherChannel fonctionne correctement
- STP protège contre les boucles
- Les ACL appliquent les règles prévues
- Les équipements peuvent être administrés de manière sécurisée
- Les tests de panne démontrent la résilience de l'architecture
