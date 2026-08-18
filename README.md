# Secure Multisite Network Infrastructure

## Présentation

Projet personnel de conception et de simulation d'une
infrastructure réseau multisite sécurisée et hautement disponible.

L'objectif est de concevoir une architecture représentant une
entreprise disposant d'un siège et d'une agence distante.

Le projet couvre la segmentation réseau, le routage, la sécurité,
la redondance et l'interconnexion des différents sites.

---

## Objectifs

- Concevoir une architecture réseau d'entreprise
- Segmenter le réseau avec des VLAN
- Mettre en place le routage inter-VLAN
- Déployer OSPF
- Mettre en place une architecture redondante
- Sécuriser les communications avec des ACL
- Mettre en œuvre EtherChannel et STP
- Mettre en place HSRP pour la haute disponibilité
- Interconnecter le siège et l'agence
- Tester et documenter l'infrastructure

---

## Architecture

### Siège

- VLAN 10 — Administration
- VLAN 20 — Employés
- VLAN 30 — IT
- VLAN 40 — RH
- VLAN 50 — Direction
- VLAN 99 — Management

### Agence distante

- VLAN 10 — Administration
- VLAN 40 — RH
- VLAN 99 — Management

---

## Technologies

- Cisco Packet Tracer
- VLAN
- 802.1Q
- Switching Layer 3
- STP
- EtherChannel / LACP
- HSRP
- OSPF
- ACL
- NAT/PAT
- DHCP
- SSH
- Port Security
- BPDU Guard

---

## Sécurité

L'infrastructure utilise une segmentation basée sur les VLAN
et des ACL afin de contrôler les communications entre les
différents services.

Le VLAN Management est réservé à l'administration des équipements.

Des mécanismes de sécurisation des ports et des accès
d'administration seront également mis en œuvre.

---

## Haute disponibilité

L'architecture intègre plusieurs mécanismes de redondance :

- Deux switches Layer 3 au niveau du cœur
- Deux switches d'accès
- Liens redondants
- EtherChannel
- STP
- HSRP
- Plusieurs chemins de routage avec OSPF

---

## Tests

Les tests porteront notamment sur :

- Connectivité inter-VLAN
- Routage OSPF
- Communication Siège ↔ Agence
- Fonctionnement des ACL
- Fonctionnement de HSRP
- Fonctionnement d'EtherChannel
- Résilience des liens
- Sécurité des ports

---

## Documentation

La documentation complète du projet se trouve dans le dossier
`docs/`.

---

## Auteur

**Abd’Fadhel ADAM**

Projet personnel — Réseaux & Cybersécurité
