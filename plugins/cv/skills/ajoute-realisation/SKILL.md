---
name: ajoute-realisation
description: Ajoute ou corrige une réalisation, une expérience ou une compétence dans la base cv-base de la personne. Utiliser dès qu'on dit « ajoute au CV », « note ça pour mon CV », « à garder pour mon CV », qu'on raconte un projet terminé, un chiffre d'impact ou une victoire pro à conserver, ou qu'on corrige une info de sa base (date, chiffre, stack).
---

# Ajouter à la base cv-base

Lire `../../references/base.md` (structure, frontmatter, règles communes) et le `CLAUDE.md` de la base.

## Étapes

1. Rattacher à une expérience (`experiences/*.md`) ou à `perso`. Nouveau poste : créer le fichier d'expérience.
2. Copier `templates/realisation.md` vers `realisations/<experience>-<slug>.md` (slug court, kebab-case).
3. Rédiger à partir de ce qui a été dit : Contexte, Ce que j'ai fait, Résultat, stack, tags, visibilité. Demander la visibilité seulement si le sujet semble confidentiel.
4. « Ligne CV » : une phrase, verbe d'action, chiffre en gras si possible. « Pitch oral » si c'est un sujet d'entretien.
5. Chiffre d'impact manquant : poser UNE question avant d'écrire. Sans réponse : `statut: a-completer`.
6. Lier la réalisation dans la section « Réalisations » de l'expérience ; mettre à jour `competences.md` (avec la preuve) et `A-COMPLETER.md` si besoin.
7. Correction d'un fichier existant : modifier en place, ne rien supprimer sans demande.

## Écrire selon la surface

- **Claude Code** : écrire les fichiers, montrer le diff, commit `feat(realisation): <titre>` ou `fix(<fichier>): <quoi>`, push.
- **claude.ai** (pas d'écriture GitHub) : livrer le fichier prêt à coller et le lien d'édition pré-rempli `https://github.com/<owner>/<repo>/new/main/realisations?filename=<id>.md`, ou `.../edit/main/<chemin>` pour une correction.
