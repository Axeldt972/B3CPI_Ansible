# Ansible — Projet Fil Rouge SOC | Groupe 3 | B3 CPI 2025-2026

Playbooks Ansible pour l'infrastructure SOC multi-VLAN du Groupe 3.

## Architecture

| VM | VLAN | IP cible |
|----|------|----------|
| G3-pfSense | — | 192.168.30.1 |
| G3-SRV-AD | VLAN10 | 10.3.10.10 |
| G3-workstation | VLAN20 | 10.3.20.10 |
| G3-SRV-APP | VLAN30 | 10.3.30.10 |
| G3-WAZUH | VLAN40 | 10.3.40.10 |
| G3-SURICATA | VLAN50 | 10.3.50.10 |

## Prérequis

```bash
pip install ansible
ansible-galaxy collection install community.general
```

## Configuration

### 1. Vault (credentials)

```bash
cp vault.yml.example group_vars/all/vault.yml
# Éditer vault.yml avec les vrais mots de passe
ansible-vault encrypt group_vars/all/vault.yml
```

### 2. Lancer un playbook

```bash
ansible-playbook -i inventory.ini playbooks/<nom>.yml --ask-vault-pass
```

## Playbooks

| Fichier | Rôle |
|---------|------|
| `01-update-all.yml` | Mise à jour APT de toutes les VMs Linux |
| `02-configure-network.yml` | Configuration `/etc/hosts` et DNS (pfSense) |
| `06-hardening.yml` | Durcissement SSH, fail2ban, sysctl, mises à jour auto |

## Sécurité

- Les credentials sont chiffrés via **ansible-vault** (`group_vars/all/vault.yml`)
- `vault.yml` est exclu du dépôt (`.gitignore`)
- Utiliser `vault.yml.example` comme modèle

## Auteur

Axel DUQUET — Chef de projet Groupe 3 — B3 CPI 2025-2026
