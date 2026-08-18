# Besoins et contraintes

## 1. Besoins fonctionnels

L'infrastructure doit permettre aux utilisateurs du siège et de
l'agence d'accéder aux ressources nécessaires à leur activité,
tout en respectant les règles de segmentation et de sécurité.

Les principaux besoins sont :

- Connecter les différents services de l'entreprise
- Séparer les services par VLAN
- Permettre les communications nécessaires entre les VLAN
- Permettre l'accès à Internet
- Interconnecter le siège et l'agence
- Assurer la continuité du service en cas de panne
- Permettre l'administration sécurisée des équipements
- Contrôler les communications entre les différents réseaux

---

## 2. Besoins de segmentation

Chaque service doit être isolé dans son propre VLAN lorsque cela
est nécessaire.

### Siège

| VLAN | Service |
|---:|---|
| 10 | Administration |
| 20 | Employés |
| 30 | IT |
| 40 | RH |
| 50 | Direction |
| 99 | Management |

### Agence

| VLAN | Service |
|---:|---|
| 10 | Administration |
| 40 | RH |
| 99 | Management |

Cette segmentation permet de réduire le domaine de broadcast,
d'améliorer l'organisation du réseau et de renforcer la sécurité.

---

## 3. Besoins de communication

Les communications entre les différents VLAN doivent être
contrôlées selon les besoins professionnels.

### Communications autorisées

- Les utilisateurs peuvent accéder aux services nécessaires
- Le service IT peut administrer les équipements
- Les équipements peuvent communiquer avec les services
  d'infrastructure nécessaires
- Le siège peut communiquer avec l'agence selon les règles
  définies

### Communications interdites

- Les utilisateurs ne doivent pas accéder directement au VLAN
  Management
- Les services ne doivent pas accéder librement aux autres VLAN
- Les postes utilisateurs ne doivent pas administrer les
  équipements réseau

Le contrôle sera réalisé à l'aide d'ACL.

---

## 4. Besoins de haute disponibilité

L'infrastructure doit limiter les interruptions de service
causées par une panne unique.

Les principaux mécanismes prévus sont :

- Deux switches Layer 3 au niveau du cœur
- Deux switches d'accès
- Liens redondants
- EtherChannel / LACP
- STP
- HSRP
- Routage OSPF

### Objectif

Une panne d'un lien ou d'un équipement critique ne doit pas
entraîner une interruption complète du réseau lorsque la
redondance prévue permet une continuité de service.

---

## 5. Besoins de routage

Le réseau doit permettre une communication entre les différents
réseaux IP nécessaires au fonctionnement de l'entreprise.

Le routage inter-VLAN sera assuré par les switches Layer 3.

OSPF sera utilisé afin de :

- Découvrir dynamiquement les réseaux
- Échanger les routes
- Adapter le routage en cas de modification de la topologie
- Exploiter plusieurs chemins lorsque cela est possible

---

## 6. Besoins de sécurité

La sécurité de l'infrastructure repose sur plusieurs niveaux.

### Sécurité des accès

- Utilisation de SSH pour l'administration
- Protection des accès privilégiés
- Mots de passe chiffrés
- Désactivation des ports inutilisés

### Sécurité des ports

- Port Security
- BPDU Guard
- PortFast sur les ports utilisateurs lorsque nécessaire

### Sécurité du routage

- ACL entre les différents VLAN
- Restriction des accès au VLAN Management
- Contrôle des flux entre les sites

---

## 7. Besoins d'administration

Le VLAN 99 est réservé à l'administration des équipements réseau.

Les équipements suivants devront pouvoir être administrés :

- Switches Layer 3
- Switches d'accès
- Routeurs

L'administration devra être réalisée via SSH.

Les interfaces de management ne devront pas être accessibles
librement depuis les VLAN utilisateurs.

---

## 8. Besoins liés au WAN

Le siège et l'agence doivent pouvoir communiquer au travers
d'une liaison WAN simulée.

Le routage entre les deux sites sera assuré par OSPF.

Dans une évolution vers une infrastructure réelle, la liaison
pourra être sécurisée par un VPN site-à-site.

---

## 9. Contraintes techniques

Le projet doit être réalisable dans un environnement de
simulation avec Cisco Packet Tracer.

Les fonctionnalités principales doivent donc être compatibles
avec les équipements disponibles dans Packet Tracer.

Les fonctionnalités non disponibles dans Packet Tracer seront
documentées comme des évolutions possibles.

---

## 10. Contraintes de dimensionnement

Le siège est dimensionné pour environ 100 utilisateurs.

Le réseau doit être conçu de manière à permettre une évolution
future du nombre de postes sans devoir modifier complètement
l'architecture.

Les plans d'adressage devront donc prévoir une capacité
suffisante pour les futurs besoins.

---

## 11. Contraintes de documentation

Chaque élément important de l'infrastructure devra être
documenté :

- Fonction des équipements
- VLAN
- Adressage IP
- Routage
- Sécurité
- Redondance
- Tests
- Résultats

Les configurations utilisées dans la maquette devront être
conservées dans le dépôt GitHub.

---

## 12. Contraintes de validation

Chaque fonctionnalité devra être testée avant d'être considérée
comme opérationnelle.

Les tests devront notamment vérifier :

- VLAN
- Trunk
- Routage inter-VLAN
- OSPF
- HSRP
- EtherChannel
- STP
- ACL
- SSH
- Communication WAN
- Résilience en cas de panne

---

## 13. Limites du projet

La maquette Packet Tracer représente une simulation pédagogique
d'une infrastructure d'entreprise.

Elle ne reproduit pas toutes les fonctionnalités d'une
infrastructure réelle.

Les solutions suivantes pourront faire l'objet d'une évolution
ultérieure :

- pfSense
- OpenVPN
- Reverse Proxy
- DMZ réelle
- Supervision avancée
- Centralisation des logs

L'objectif principal de la maquette est de démontrer la maîtrise
des concepts réseau étudiés durant la formation.
