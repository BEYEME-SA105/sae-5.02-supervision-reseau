# Suivi de l'idempotence — SAE 5.02

## Rôle common

- **Date du test :** 27 octobre 2026
- **Playbook :** `playbooks/01_common.yml`
- **Machine testée :** Kali Linux

### Première exécution
- `ok=5`
- `changed=1`
- `unreachable=0`
- `failed=0`

Le cache APT a été mis à jour. Aucun échec n'a été constaté.

### Deuxième exécution
- `ok=5`
- `changed=0`
- `unreachable=0`
- `failed=0`

### Résultat
Succès sur Kali Linux. La deuxième exécution n'a entraîné aucune modification (`changed=0`) et aucune erreur n'a été détectée (`failed=0`). Le rôle `common` est idempotent sur cette machine.

**Remarque :** des avertissements de dépréciation Ansible apparaissent concernant l'accès aux faits système. Ils n'ont pas empêché l'exécution du playbook.
