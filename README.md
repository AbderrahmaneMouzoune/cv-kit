# cv-kit

Marketplace de plugins Claude contenant le plugin **cv** (skills `generate-cv`, `ajoute-realisation`, `init-base`).

Le plugin ne contient aucune donnée : chaque personne a son propre repo privé `cv-base`, créé depuis `cv-base-template`.

## Installer

`YouzouneDev` est un compte GitHub personnel (pas une organisation) : l'accès aux repos privés passe par les collaborateurs du repo, et claude.ai lit le repo via la Claude GitHub App installée sur ce compte.

- **claude.ai (organisation)** : Organization settings > Plugins, ajouter la marketplace GitHub `YouzouneDev/cv-kit`, activer `cv` pour les membres concernés.
- **Claude Code** : automatique dans un repo créé depuis `cv-base-template` (voir son `.claude/settings.json`), sinon `/plugin marketplace add YouzouneDev/cv-kit` puis `/plugin install cv@cv-kit`.

## Faire évoluer

Modifier les skills ici, augmenter `version` dans `plugins/cv/.claude-plugin/plugin.json`, push. Valider avec `claude plugin validate .`.
