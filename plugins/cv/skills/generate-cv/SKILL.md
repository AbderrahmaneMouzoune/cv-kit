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
   - `statut: a-completer` : utilisable seulement sans ses parties `[à confirmer]` ;
   - classer toutes les réalisations éligibles par pertinence pour l'offre ou l'angle : recouvrement `tags` + `stack`, puis force des `metriques` ;
   - les ajouter dans cet ordre jusqu'à remplir les pages cibles (voir « Remplissage » en 4) : c'est la place réellement disponible qui fixe le nombre de lignes, pas un quota par poste ;
   - plancher : 2 lignes par poste ayant au moins 2 réalisations éligibles (sinon toutes celles qu'il a), pour qu'aucun poste ne paraisse vide ;
   - à pertinence égale, un poste ancien passe après un poste récent : c'est un ordre de priorité, pas un plafond.
5. Compétences : `competences.md` réordonné selon l'offre, uniquement le prouvé, rien de la section « À ne pas mettre ».

## 3. Écrire

Règles communes de `references/base.md`, plus : dates exactement celles de `experiences/`, localisation et coordonnées de `identite.md`, reformuler sans enrichir.

## 4. Produire

1. Partir de `assets/cv-template.html`. Appliquer `charte.couleur` et `charte.police` de `identite.md` (défaut `#141414`, sans-serif). Si `cv/` contient un CV récent, s'aligner sur sa mise en page.
2. PDF via Chromium headless (Playwright `page.pdf(format="A4", print_background=True)`). Rien de coupé. Réduire la sélection plutôt que la police sous 9 pt.
3. Remplissage :
   - cible par défaut : 2 pages, dernière page remplie au moins aux trois quarts ;
   - si le contenu pertinent ne remplit pas 2 pages, passer à 1 page bien remplie plutôt que livrer une page à moitié vide ;
   - si 1 page est demandée : viser une page pleine ;
   - mesurer après chaque PDF : hauteur du contenu en média print (`page.emulate_media(media="print")`, puis `document.body.scrollHeight`) rapportée à la hauteur utile d'une page (A4 moins les marges `@page`, environ 1017 px pour 297 mm moins 28 mm à 96 dpi) ; taux de la dernière page = reste de la division / hauteur utile ;
   - si le taux est trop faible : ajouter la réalisation pertinente suivante (ou un bloc projets perso ou missions freelance), régénérer et remesurer, 3 itérations maximum ;
   - si un ajout fait déborder d'une page la cible, le retirer et le noter comme « dépassement de page ».
4. Version `cv.txt` pour les formulaires.
5. Contrôles avant livraison (bloquants) : zéro tiret cadratin (U+2014) dans le HTML et le TXT ; chaque chiffre d'impact du CV se retrouve dans `realisations/` ; aucune réalisation `entretien` ou `interne` utilisée ; nombre de pages respecté. Un frontmatter YAML illisible (ex. `titre:` non quoté contenant « : ») ne doit pas faire ignorer la réalisation en silence : la lire quand même et signaler le fichier à corriger.
6. Nommer `CV-<Prenom>-<Nom>-<Entreprise>-<AAAA-MM>.pdf` ; livrer PDF puis HTML et TXT (`present_files` dans claude.ai).

## 5. Après livraison (court)

- **Compte rendu honnête** : taux de remplissage de la dernière page ; liste des réalisations éligibles non retenues avec la vraie raison : « moins pertinente pour l'angle », « dépassement de page » (seulement si l'ajouter faisait réellement déborder) ou « redondante avec X ». Ne jamais écrire « faute de place » sans débordement constaté.
- **Écarts** : exigences de l'offre non couvertes par la base, sans les combler. Demander si une expérience réelle existe ; si oui, enchaîner avec `ajoute-realisation`.
- **Archivage** dans `cv/<AAAA-MM>-<entreprise>/` : en Claude Code, commit `docs(cv): <entreprise>` ; depuis claude.ai, lien d'upload `https://github.com/<owner>/<repo>/upload/main/cv/<AAAA-MM>-<entreprise>` (owner/repo de la base).
- **Incohérences** repérées (dates qui se chevauchent, chiffre sans source) : une ligne pour `A-COMPLETER.md`.
