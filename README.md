# SOC G3 — Ansible Automatisation

Projet fil rouge B3 CPI — Keyce Academy Martinique 2025-2026
Axel DUQUET — Chef de projet

## Playbooks

| Playbook | Rôle |
|----------|------|
| 01-update-all.yml | Mise à jour système toutes VMs |
| 02-configure-network.yml | Configuration réseau de base |
| 06-hardening.yml | Durcissement SSH |

## Accès

```bash
ansible all -m ping
ansible-playbook playbooks/06-hardening.yml --diff
```
