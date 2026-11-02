# Format d'une base cv-base

Chaque personne a SON repo privé, créé depuis le template `cv-base-template`. Le plugin ne contient aucune donnée personnelle.

## Repérer une base

Un dossier est une base si on y trouve `profil/identite.md` ET `realisations/`. Le `CLAUDE.md` de la base contient les règles personnelles de son propriétaire : elles s'ajoutent aux règles du plugin et priment en cas de conflit.

## Où la trouver selon la surface

1. **Claude Code** : dossier courant (ou parent). Faire `git pull` avant de lire.
2. **Project claude.ai** : le repo de la personne synchronisé en knowledge du Project (« + » > GitHub). Les fichiers sont dans le contexte.
3. **Uploads** : zip ou `.md` dans `/mnt/user-data/uploads`.
4. **Rien trouvé** : le repo est privé, `git clone` et `web_fetch` échouent. Ne jamais reconstituer la base depuis la mémoire, l'historique ou un ancien CV. Demander en une phrase de synchroniser son repo au Project, ou de lancer la demande depuis Claude Code dans son repo. S'il n'a pas encore de base : proposer le skill `init-base`.

Une seule base par session. Si plusieurs sont visibles (ex. Project partagé), demander laquelle utiliser et ne jamais mélanger les données de deux personnes.

## Structure

| Chemin | Contenu |
|---|---|
| `CLAUDE.md` | Règles personnelles (ex. sujets à ne pas mettre en avant) |
| `profil/identite.md` | Frontmatter : `nom`, `prenom`, `titre`, `localisation`, `email`, `telephone`, `linkedin`, `github`, `site`, `langue_defaut`, `charte.couleur`, `charte.police` |
| `profil/positionnements.md` | Angles de CV (ex. backend, frontend, lead) : titre + accroche |
| `experiences/<slug>.md` | Un poste : entreprise, intitulé, dates, lieu, contexte, réalisations rattachées |
| `realisations/<experience>-<slug>.md` | Une réalisation (frontmatter ci-dessous + sections) |
| `projets-perso/` | Projets personnels |
| `competences.md` | Compétences + preuve ; section « À ne pas mettre » |
| `formation.md` | Diplômes, certifications, langues |
| `A-COMPLETER.md` | Trous et incohérences connus |
| `templates/realisation.md` | Gabarit |
| `medias/<id>/` | Visuels, avec visibilité |
| `cv/<AAAA-MM>-<entreprise>/` | Archives des CV générés |
| `prive/` | Hors CV : jamais lu par `generate-cv` |

## Frontmatter d'une réalisation

- `id` : nom du fichier sans `.md`
- `titre`, `experience` (slug ou `perso`), `periode` (`AAAA`, `AAAA-MM` ou intervalle)
- `tags` : `backend, frontend, archi, aws, perf, ia, ml, data, seo, produit, qualite, lead, outillage, ops, cout, accessibilite, communication` (extensible)
- `stack` : technos réellement utilisées
- `metriques` : chiffres sourcés
- `visibilite` : `cv` (écrit sur le CV), `entretien` (à raconter, pas à écrire), `interne` (ne jamais diffuser)
- `statut` : `complet` ou `a-completer`

Sections : Contexte, Ce que j'ai fait, Résultat, Ligne CV, Pitch oral.

## Règles communes (toutes les bases)

1. Ne jamais inventer un chiffre, une techno, une date ou une responsabilité. Inconnu = `[à confirmer]` + entrée dans `A-COMPLETER.md`.
2. Jamais de tiret cadratin (caractère U+2014). Deux-points, virgule, parenthèses.
3. Un chiffre reste attaché à la réalisation qui le porte.
4. Distinguer « j'ai fait » de « l'équipe a fait » (« contribution à », « co-conception »).
5. Ton sobre : verbes d'action, pas d'adjectifs vendeurs.
6. Pas de techno non pratiquée dans les compétences.
