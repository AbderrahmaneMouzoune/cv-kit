---
name: generate-cv
description: Génère un CV ciblé (HTML + PDF + TXT, ATS friendly) à partir de la base de connaissance cv-base de la personne (son repo Git privé), jamais de mémoire ni d'anciens CV. Utiliser dès qu'on demande un CV, de « refaire / adapter / mettre à jour mon CV », qu'on envoie une fiche de poste ou une offre de mission à laquelle postuler, qu'un recruteur réclame un CV, ou qu'on veut un CV par angle (backend, frontend, lead...), même sans dire « CV » (ex. « prépare ma candidature chez X »).
---

# Générer un CV depuis cv-base

Lire d'abord `../../references/base.md` : où trouver la base, sa structure, les règles communes. La base de la personne est la SEULE source : la mémoire, l'historique et les anciens CV contiennent des erreurs déjà corrigées dans la base.

## 1. Charger la base (bloquant)

Suivre « Où la trouver » dans `references/base.md`. Sans base, s'arrêter là (sauf analyse de l'offre, qu'on peut préparer). Lire le `CLAUDE.md` de la base : ses règles personnelles s'appliquent. Ne jamais ouvrir `prive/`.

## 2. Cibler

1. Entrée : offre (URL à fetcher, texte, PDF) ou angle. Si rien, demander l'angle en une question.
2. Extraire : intitulé, stack exigée, responsabilités, mots-clés ATS, séniorité, langue (sinon `langue_defaut`).
3. Angle le plus proche dans `positionnements.md`. Le titre reprend l'intitulé de l'offre s'il est cohérent avec le parcours.
4. Réalisations :
   - uniquement `visibilite: cv` ;
   - classer par recouvrement `tags` + `stack` avec l'offre, puis par force des `metriques` ;
   - 3 à 5 lignes par poste récent, 2 à 3 pour les anciens ;
   - `statut: a-completer` : utilisable seulement sans ses parties `[à confirmer]`.
5. Compétences : `competences.md` réordonné selon l'offre, uniquement le prouvé, rien de la section « À ne pas mettre ».

## 3. Écrire

Règles communes de `references/base.md`, plus : dates exactement celles de `experiences/`, localisation et coordonnées de `identite.md`, reformuler sans enrichir.

## 4. Produire

1. Partir de `assets/cv-template.html`. Appliquer `charte.couleur` et `charte.police` de `identite.md` (défaut `#141414`, sans-serif). Si `cv/` contient un CV récent, s'aligner sur sa mise en page.
2. PDF via Chromium headless (Playwright `page.pdf(format="A4", print_background=True)`). Vérifier : 2 pages max (1 si demandé), rien de coupé. Réduire la sélection plutôt que la police sous 9 pt.
3. Version `cv.txt` pour les formulaires.
4. Contrôles avant livraison (bloquants) : zéro tiret cadratin (U+2014) dans le HTML et le TXT ; chaque chiffre d'impact du CV se retrouve dans `realisations/` ; aucune réalisation `entretien` ou `interne` utilisée ; nombre de pages respecté. Un frontmatter YAML illisible (ex. `titre:` non quoté contenant « : ») ne doit pas faire ignorer la réalisation en silence : la lire quand même et signaler le fichier à corriger.
5. Nommer `CV-<Prenom>-<Nom>-<Entreprise>-<AAAA-MM>.pdf` ; livrer PDF puis HTML et TXT (`present_files` dans claude.ai).

## 5. Après livraison (court)

- **Écarts** : exigences de l'offre non couvertes par la base, sans les combler. Demander si une expérience réelle existe ; si oui, enchaîner avec `ajoute-realisation`.
- **Archivage** dans `cv/<AAAA-MM>-<entreprise>/` : en Claude Code, commit `docs(cv): <entreprise>` ; depuis claude.ai, lien d'upload `https://github.com/<owner>/<repo>/upload/main/cv/<AAAA-MM>-<entreprise>` (owner/repo de la base).
- **Incohérences** repérées (dates qui se chevauchent, chiffre sans source) : une ligne pour `A-COMPLETER.md`.
