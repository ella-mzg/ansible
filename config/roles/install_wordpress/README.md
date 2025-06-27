# Ansible Role: install_wordpress

## Description

Ce rôle Ansible installe et configure automatiquement un site WordPress avec Apache, PHP et MariaDB. Il est compatible avec les systèmes **Debian-based (Ubuntu)** et **RedHat-based (Rocky Linux)**, en environnement classique ou conteneurisé.

## Fonctionnalités

- Installation conditionnelle des paquets nécessaires (Apache/HTTPD, PHP, MariaDB)
- Démarrage compatible container ou VM classique
- Sécurisation de l'installation MariaDB
- Création de la base de données WordPress
- Déploiement et configuration automatique de WordPress
- Support des handlers et des variables

## Variables par défaut

Les variables peuvent être surchargées dans votre playbook :

```yaml
apache_service: apache2 (ou httpd)
apache_service_path: /usr/sbin/apache2 (ou /usr/sbin/httpd)

wp_db_name: wordpress
wp_db_user: example
wp_db_password: examplePW
wp_db_root_password: examplerootPW
```

Les paquets sont gérés en fonction de la distribution avec `ubuntu_packages` et `rocky_packages`.

## Utilisation

Exemple de playbook :

```yaml
- name: Déployer WordPress
  hosts: all
  roles:
    - role: ella-mzg.install_wordpress
```

## Structure du rôle

```
install_wordpress/
├── defaults/
│   └── main.yml
├── handlers/
│   └── main.yml
├── meta/
│   └── main.yml
├── tasks/
│   ├── main.yml
│   ├── install-wordpress.yml
│   └── secure-mariadb.yml
├── templates/
│   └── wp-config.php.j2
└── README.md
```

## Compatibilité

- Testé avec Ubuntu et Rocky Linux
- Fonctionne en mode systemd ou conteneur (Docker/LXC)

## Installation depuis Galaxy

```bash
ansible-galaxy role install ella-mzg.install_wordpress
```

## Licence

MIT

## Auteur

Ella Mzoughi
