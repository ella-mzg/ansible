# Role Name

Installe et configure automatiquement un serveur WordPress avec Apache, PHP et MariaDB sur les systèmes Debian et RedHat (y compris dans des environnements conteneurisés).

## Requirements

Aucun prérequis spécifique, à part une connexion SSH fonctionnelle et `python3` sur la machine cible.
Role Variables

---

## Role Variables

Variables personnalisables dans `defaults/main.yml` :

```yaml
wp_db_name: wordpress
wp_db_user: example
wp_db_password: examplePW
wp_db_root_password: examplerootPW
```

## License

MIT

## Author Information

Ella Mzoughi
