# 🖥️ Windows Server 2022 Lab — Infrastructure AD DS, DNS & DHCP

> **Projet d'Accompagnement Personnalisé (AP) / Portfolio Technique**  
> **Environnement :** VirtualBox | **OS Serveur :** Windows Server 2022 Datacenter  
> **Auteur :** Jean-Prem

---

## 📌 Présentation du Projet

Ce projet consiste en la mise en place et la configuration complète d'une infrastructure réseau virtualisée d'entreprise. L'objectif est de centraliser la gestion des utilisateurs via **Active Directory (AD DS)** et d'automatiser l'attribution dynamique des adresses IP via le service **DHCP**.

---

## ⚙️ Spécifications Techniques & Maquette Réseau

| Composant | Configuration / Valeur |
| :--- | :--- |
| **Nom du Serveur (DC)** | `SRV-DC01` |
| **Domaine AD DS** | `int.utec.local` |
| **Adresse IP Fixe (Static)** | `192.168.1.10 /24` |
| **Rôles installés** | AD DS, DNS, DHCP |
| **Nom de l'étendue DHCP** | `Reseau-AP` |
| **Plage DHCP (Scope)** | `192.168.1.50` à `192.168.1.200` |
| **Unité d'Organisation (OU)**| `Utilisateurs-AP` |
| **Utilisateur de test** | Pierre Dupont (`p.dupont`) |

---

## 🛠️ Étapes de Réalisation

### 1. Installation & Configuration Réseau de Base
* Déploiement d'une VM sous **Windows Server 2022** sur Oracle VirtualBox.
* Définition du nom d'hôte : `SRV-DC01`.
* Attribution d'une adresse IP statique (`192.168.1.10/24`).

### 2. Promotion du Contrôleur de Domaine & DNS
* Installation des rôles **AD DS** et **Serveur DNS**.
* Promotion du serveur en tant que contrôleur de domaine principal pour la forêt `int.utec.local`.

### 3. Configuration et Autorisation du Service DHCP
* Installation du rôle DHCP.
* **Autorisation du serveur DHCP** dans l'Active Directory.
* Création et activation de l'étendue `Reseau-AP` avec attribution automatique des options DNS.

### 4. Structuration de l'Annuaire AD DS
* Création d'une Unité d'Organisation dédiée : **`Utilisateurs-AP`**.
* Création du compte utilisateur de test : **Pierre Dupont** (`p.dupont@int.utec.local`).
* Application de la politique de sécurité des mots de passe.

---

### 1. Structure Active Directory & Compte Utilisateur
![Active Directory](docs/images/ad_ou_user.jpg)
*Création de l'OU Utilisateurs-AP et validation du compte Pierre Dupont.*

### 2. Validation du Tableau de Bord
![Dashboard](docs/images/dashboard.jpg)
*Rôles AD DS, DHCP et DNS opérationnels sur le Gestionnaire de Serveur.*
---

## 🚀 Prochaines Étapes (Roadmap)

- [ ] Déploiement d'une VM cliente (**Windows 10 / 11**).
- [ ] Test d'attribution IP automatique via DHCP (`192.168.1.X`).
- [ ] Jonction de la VM cliente au domaine `int.utec.local`.
- [ ] Validation de la première ouverture de session utilisateur avec `p.dupont`.
