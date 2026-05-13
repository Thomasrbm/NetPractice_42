<div align="center">

# NetPractice

**Projet de l'École 42 — Introduction pratique au réseau TCP/IP**

[![42 School](https://img.shields.io/badge/42-School-000000?style=flat-square&logo=42&logoColor=white)](https://42.fr)
[![Note](https://img.shields.io/badge/Note-100%2F100-success?style=flat-square)](#)
[![Language](https://img.shields.io/badge/Langage-Networking-blue?style=flat-square)](#)
[![Status](https://img.shields.io/badge/Statut-Terminé-brightgreen?style=flat-square)](#)

</div>

---

## Sommaire

- [À propos](#à-propos)
- [Objectifs pédagogiques](#objectifs-pédagogiques)
- [Concepts couverts](#concepts-couverts)
- [Structure du projet](#structure-du-projet)
- [Progression des niveaux](#progression-des-niveaux)
- [Mémo technique](#mémo-technique)
- [Lancement](#lancement)
- [Auteur](#auteur)
- [Licence](#licence)

---

## À propos

**NetPractice** est un projet de l'école **42** axé sur la résolution de problèmes pratiques de configuration réseau. À travers **10 niveaux** de difficulté croissante, l'étudiant doit configurer des architectures réseau (machines, routeurs, switches, internet) afin que la communication s'établisse correctement entre les différents équipements.

Le projet ne demande pas d'écrire du code, mais d'**appliquer les bons principes de l'adressage IP, du masquage de sous-réseau et du routage** pour faire fonctionner des topologies réseau de plus en plus complexes.

---

## Objectifs pédagogiques

- Comprendre la **structure d'une adresse IPv4** et la division réseau/hôte
- Maîtriser les **masques de sous-réseau** et la notation **CIDR**
- Savoir construire et lire une **table de routage**
- Identifier la différence entre **switch**, **routeur**, **modem** et **box**
- Connaître les **plages d'adresses privées** (RFC 1918) et publiques
- Diagnostiquer un problème de connectivité dans une topologie réseau

---

## Concepts couverts

| Domaine | Notions clés |
|---------|--------------|
| **Adressage IP** | IPv4, partie réseau / partie hôte, adresse de broadcast, adresse de réseau |
| **Masques** | Notation CIDR (`/8` → `/30`), masque décimal, calcul de sous-réseaux |
| **Routage** | Table de routage, route par défaut, passerelle (gateway), prochain saut |
| **Équipements** | Hôte, switch, routeur, interface, modem, box, internet |
| **Protocoles** | TCP/IP, ARP, NAT, DHCP |
| **Sécurité** | Réseaux privés vs publics, isolation par sous-réseaux |

---

## Structure du projet

```
NetPractice_42/
├── index.html              # Page d'accueil de l'outil 42
├── level1.html → level10.html
├── end.html                # Écran de fin
├── css/
│   └── netpractice.css     # Feuille de style
├── js/
│   ├── intro.js            # Script d'introduction
│   ├── level1.js → level10.js   # Logique de chaque niveau
│   ├── show.js             # Affichage des topologies
│   └── sim.js              # Simulateur réseau
├── img/                    # Iconographie (host, router, switch, internet)
└── License                 # Licence pédagogique 42
```

---

## Progression des niveaux

| Niveau | Difficulté | Thème principal |
|:------:|:----------:|-----------------|
| **1** | ★☆☆☆☆ | Configuration de base d'une IP entre deux machines |
| **2** | ★☆☆☆☆ | Masque de sous-réseau et appartenance au même réseau |
| **3** | ★★☆☆☆ | Switch et adressage cohérent |
| **4** | ★★☆☆☆ | Introduction au routeur et à la passerelle |
| **5** | ★★★☆☆ | Table de routage simple |
| **6** | ★★★☆☆ | Route par défaut et sortie vers Internet |
| **7** | ★★★★☆ | Routage entre plusieurs routeurs |
| **8** | ★★★★☆ | Topologie complexe — masque `/28` partout |
| **9** | ★★★★★ | Découpage en sous-réseaux (`/18` → `/28`) |
| **10** | ★★★★★ | Architecture finale combinant tous les concepts |

---

## Mémo technique

### Masques courants (CIDR ↔ nombre d'adresses)

| CIDR | Masque décimal | Sous-réseaux × Hôtes |
|:----:|:--------------:|:--------------------:|
| `/24` | `255.255.255.0`   | 1 × 256 |
| `/25` | `255.255.255.128` | 2 × 128 |
| `/26` | `255.255.255.192` | 4 × 64  |
| `/27` | `255.255.255.224` | 8 × 32  |
| `/28` | `255.255.255.240` | 16 × 16 |
| `/29` | `255.255.255.248` | 32 × 8  |
| `/30` | `255.255.255.252` | 64 × 4  |

### Règles d'adressage

- La **première** adresse d'un sous-réseau identifie le **réseau** lui-même
- La **dernière** adresse est réservée au **broadcast**
- Ces deux adresses ne sont **pas assignables** à une machine

### Plages d'adresses privées (RFC 1918)

```
10.0.0.0     /8     — Grandes organisations
172.16.0.0   /12    — Réseaux moyens
192.168.0.0  /16    — Réseaux domestiques
127.0.0.0    /8     — Loopback (localhost)
```

### Logique de routage

> Si l'IP de destination appartient au **même sous-réseau** → communication directe via le **switch** (adresse MAC, protocole ARP).
> Sinon → envoi au **routeur** désigné par la table de routage (route spécifique ou route par défaut).

---

## Lancement

Cloner le dépôt puis ouvrir `index.html` dans un navigateur :

```bash
git clone https://github.com/<votre-utilisateur>/NetPractice_42.git
cd NetPractice_42
xdg-open index.html   # Linux
open index.html       # macOS
```

Aucune dépendance externe n'est requise — l'outil est entièrement client-side (HTML/CSS/JavaScript).

---

## Auteur

**thomasrbm** — Étudiant à l'École 42

---

## Licence

Ce projet est fourni dans un cadre **strictement pédagogique** dans le cursus de l'école 42.
Toute duplication, modification ou utilisation hors de ce contexte (personnel, commercial, public, open source) n'est pas autorisée.

Voir le fichier [`License`](./License) pour plus de détails.
