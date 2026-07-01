# SOC G3 — Ansible Automation

Projet fil rouge B3 CPI — Keyce Academy Martinique 2025-2026  
Groupe 3 : Axel DUQUET · Julien PODEVIN · Kévin DACLINAT · Karl-Edwing TRAMIS

## Infrastructure cible

5 VMs Debian 13 sur KVM, routées par pfSense via 5 VLANs (10.3.x.0/24).  
Accès via ProxyJump IT-Server (Tailscale) + tunnels SOCAT.

## Playbooks

| Playbook | Rôle |
|----------|------|
| 01-update-all.yml | Mise à jour système toutes VMs |
| 02-configure-network.yml | Config réseau de base |
| 03-install-suricata.yml | Suricata IDS + règles ET Open |
| 04-install-wazuh-agent.yml | Wazuh Manager all-in-one + agents |
| 05-install-glpi.yml | GLPI 11.0.6 + PHP 8.4 + MariaDB |
| 06-hardening.yml | Durcissement SSH (PermitRootLogin, MaxAuthTries…) |
| 07-migrate-vlan.yml | Ajout sous-interfaces 802.1q par VM |

## Accès

```bash
# Vérification connectivité
ansible all -m ping

# Hardening SSH
ansible-playbook playbooks/06-hardening.yml --diff
