# SAE 5.02 — Supervision automatisée d'une infrastructure réseau

## Objectif
Concevoir une solution de supervision automatisée avec Docker,
Docker Compose et Ansible.

## Prérequis
- Git
- Docker et Docker Compose
- Ansible
- VMware ou équivalent

## Comment lancer
1. Configurer l'inventaire dans `inventory/hosts.yml`.
2. Vérifier l'inventaire :

   ansible -i inventory/hosts.yml all --list-hosts

3. Vérifier le playbook :

   ansible-playbook -i inventory/hosts.yml playbooks/site.yml --syntax-check

## Arborescence
- `inventory/` : inventaire des machines
- `playbooks/` : playbooks Ansible
- `roles/` : rôles réutilisables
- `docs/` : documentation technique
