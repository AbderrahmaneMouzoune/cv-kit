# cv-kit

Marketplace de plugins Claude contenant le plugin **cv** (skills `generate-cv`, `ajoute-realisation`, `init-base`).

Le plugin ne contient aucune donnée : chaque personne a son propre repo privé `cv-base`, créé depuis `cv-base-template`.

## Installer

Ce repo et `cv-base-template` sont publics (aucune donnée personnelle) : aucune invitation ni Claude GitHub App n'est nécessaire pour la marketplace. Seules les bases `cv-base` de chacun sont privées.

- **claude.ai (organisation)** : Organization settings > Plugins, ajouter la marketplace GitHub `AbderrahmaneMouzoune/cv-kit`, activer `cv` pour les membres concernés.
- **Claude Code** : automatique dans un repo créé depuis `cv-base-template` (voir son `.claude/settings.json`), sinon `/plugin marketplace add AbderrahmaneMouzoune/cv-kit` puis `/plugin install cv@cv-kit`.

## Faire évoluer

Modifier les skills ici, augmenter `version` dans `plugins/cv/.claude-plugin/plugin.json`, push. Valider avec `claude plugin validate .`.
