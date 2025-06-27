# Ansible Role: install_wordpress

## Description

Ce rôle Ansible installe automatiquement WordPress avec une base de données MariaDB sur des systèmes Ubuntu **et** Rocky Linux, qu’ils soient classiques ou conteneurisés.

Il configure :

- Apache (ou httpd)
- PHP
- MariaDB avec création de base, utilisateur et mot de passe
- WordPress dans `/var/www/html`
- Le fichier `wp-config.php` avec les bonnes valeurs
- Les permissions adéquates sur les fichiers
- Un handler pour redémarrer Apache si besoin

## Compatibilité

Support des environnements, Debian, RHEL, Docker/LXC

## Rôle disponible sur Ansible Galaxy

```bash
ansible-galaxy role install ella-mzg.install_wordpress
```

## Variables par défaut

```yaml
# Service Apache
apache_service: "{{ 'apache2' if ansible_os_family == 'Debian' else 'httpd' }}"
apache_service_path: "{{ '/usr/sbin/apache2' if ansible_os_family == 'Debian' else '/usr/sbin/httpd' }}"

# Paquets nécessaires
ubuntu_packages:
  - apache2
  - php
  - libapache2-mod-php
  - php-mysql
  - mariadb-server
  - wget
  - unzip

rocky_packages:
  - httpd
  - php
  - php-mysqlnd
  - mariadb-server
  - wget
  - unzip

# Base de données WordPress
wp_db_name: wordpress
wp_db_user: example
wp_db_password: examplePW
wp_db_root_password: examplerootPW
```

## Exemple de Playbook

```yaml
- name: Déploiement de WordPress
  hosts: all
  roles:
    - ella-mzg.install_wordpress
```

## Licence

MIT-0

## Auteur

Ella (ella-mzg)
