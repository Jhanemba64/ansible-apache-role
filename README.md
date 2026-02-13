# Déploiement Apache avec Ansible

Utiliser **Ansible** pour automatiser l’installation et la configuration d’un serveur web Apache sur la machine locale.

- Installation d’Ansible sous Ubuntu (WSL)
- Création d’un **rôle Ansible** `demo_apache`
- Installation automatique d’Apache
- Démarrage et activation du service
- Déploiement d’une page HTML
- Exécution du playbook sur `localhost`

## Après exécution du playbook :

- Apache est installé et actif
- Une page web accessible via : http://localhost


## Commande principale

```bash
ansible-playbook -i "localhost," -c local playbook-front.yml
```
