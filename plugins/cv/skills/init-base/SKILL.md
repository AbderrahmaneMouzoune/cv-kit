---
name: init-base
description: Crée la base de connaissance CV (repo cv-base) d'une personne qui n'en a pas encore, à partir de son CV actuel, de son LinkedIn collé en texte, d'un export Excel ou d'un récit. Utiliser quand quelqu'un veut « monter sa base CV », « démarrer cv-base », « importer mon CV », ou quand generate-cv ne trouve aucune base.
---

# Initialiser une base cv-base

Lire `../../references/base.md`.

1. **Créer le repo** depuis le template (privé) : `https://github.com/new?template_name=cv-base-template&template_owner=YouzouneDev&name=cv-base&visibility=private`. Lui donner le lien pré-rempli.
2. **Collecter** : CV (PDF/DOCX), LinkedIn collé en texte (la lecture automatique de LinkedIn est bloquée), Excel, récit libre.
3. **Extraire** : identité, postes, réalisations (une par fichier), projets perso, compétences, formation. Ne rien inventer : tout chiffre ou date incertain devient `[à confirmer]`.
4. **Croiser les sources** et lister les incohérences (dates qui se chevauchent, intitulés différents) dans `A-COMPLETER.md`.
5. **Faire valider** le contenu dans un document lisible (pas directement le zip), réalisation par réalisation, avec la visibilité proposée.
6. **Livrer** : en Claude Code, écrire et pousser dans le repo ; sinon un zip à la structure du template.
7. **Brancher** : rappeler de synchroniser le repo dans son Project claude.ai (« + » > GitHub) pour générer ses CV depuis le chat.
