# Rôle `demo_apache`

Installe Apache, le démarre et l'active au boot, puis publie une page d'accueil générée
depuis un template Jinja2.

## Plateformes

Famille Debian (`apache2`), testée en CI sur Ubuntu 24.04. Les noms de paquet et de service
de la famille RedHat (`httpd`) sont aussi pris en charge.

## Variables

| Variable | Défaut | Usage |
|---|---|---|
| `app_title` | `Demo Apache - généré par Ansible` | Titre de la page d'accueil |
| `web_root` | `/var/www/html` | Dossier publié par Apache |

## Exemple

```yaml
- name: Serveurs web
  hosts: web
  become: true
  roles:
    - role: demo_apache
      vars:
        app_title: Mon site
```

## Licence

MIT
