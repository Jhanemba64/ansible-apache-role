# Déploiement Apache avec Ansible

[![CI](https://github.com/Jhanemba64/ansible-apache-role/actions/workflows/ci.yml/badge.svg)](https://github.com/Jhanemba64/ansible-apache-role/actions/workflows/ci.yml)

Rôle **Ansible** `demo_apache` qui automatise l'installation et la configuration d'un serveur
web Apache :

- installation d'Apache (`apache2` sur Debian/Ubuntu, `httpd` sur la famille RedHat) ;
- démarrage du service et activation au boot ;
- publication d'une page d'accueil générée depuis un template Jinja2 ;
- redémarrage d'Apache par un handler, uniquement quand la page change.

Variables et exemple d'utilisation : [demo_apache/README.md](demo_apache/README.md).

## Utilisation

```bash
ansible-playbook -i "localhost," -c local playbook-front.yml
```

Apache est alors actif et la page est servie sur http://localhost.

## Intégration continue

Chaque push et chaque pull request passent par le workflow [`ci.yml`](.github/workflows/ci.yml) :

1. **ansible-lint** : bonnes pratiques Ansible, métadonnées du rôle et syntaxe YAML ;
2. **exécution réelle** du playbook sur le runner GitHub (Ubuntu 24.04) ;
3. **idempotence** : un second passage ne doit rien modifier (`changed=0`) ;
4. **vérification** que la page générée est bien servie par Apache.

Les actions GitHub sont épinglées par SHA de commit et mises à jour chaque mois par Dependabot.

## Structure

```
.
├── playbook-front.yml        # playbook d'exemple (localhost)
├── demo_apache/
│   ├── tasks/main.yml        # installation, service, page d'accueil
│   ├── handlers/main.yml     # redémarrage d'Apache
│   ├── templates/index.html.j2
│   ├── defaults/main.yml     # variables surchargeables
│   └── meta/main.yml         # métadonnées Galaxy
└── .github/                  # workflow CI et configuration Dependabot
```

## Licence

[MIT](LICENSE)
