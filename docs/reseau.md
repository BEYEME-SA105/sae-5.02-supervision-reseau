# Documentation Réseau - SAE 5.02 Supervision Réseau

Cette documentation présente la correction du plan d'adressage initialement prévu (`192.168.50.x`) afin de l'adapter à la réalité du réseau physique de l'hôte (Mac en mode Accès par pont / Bridged).

## Informations Réseau Réelles
- **Passerelle (Gateway) :** `192.168.1.254`
- **Adresse de Broadcast :** `192.168.1.255`
- **Interface physique hôte (Mac) :** `en0` (Wi-Fi)

## Inventaire et Plan d'Adressage Statique
Les adresses dynamiques DHCP ont été remplacées par des configurations statiques situées en dehors de la plage DHCP classique pour éviter toute rupture de l'inventaire de supervision.

| Machine | Système d'exploitation | Interface VM | Ancienne IP | Nouvelle IP (Fixe) |
| :--- | :--- | :--- | :--- | :--- |
| **Kali** | Kali Linux | `eth0`  | `192.168.1.21` | **`192.168.1.232`** |
| **VM2** | Ubuntu Server | `enp0s3` | `192.168.1.76` | **`192.168.1.230`** |
| **VM3** | Ubuntu Server | `enp0s3` | `192.168.1.7` | **`192.168.1.231`** |

## Procédure de Configuration Appliquée

### 1. Ubuntu Server (VM2 & VM3) via Netplan
La configuration a été figée dans le fichier `/etc/netplan/00-installer-config.yaml` avec l'adressage statique et la route par défaut vers la passerelle réelle (`192.168.1.254`). 
Application via la commande : `sudo netplan apply`.

### 2. Kali Linux via NetworkManager
L'ancienne adresse IP dynamique fournie par le DHCP (`.21`) a été nettoyée pour éviter les conflits d'interface. La carte a été configurée manuellement sur l'IP statique `.232`.

## Validation
Des tests croisés de connectivité (`ping`) ont été effectués avec succès entre toutes les machines virtuelles ainsi que vers la passerelle Internet. Le réseau est fonctionnel et prêt pour le déploiement des outils de supervision.
