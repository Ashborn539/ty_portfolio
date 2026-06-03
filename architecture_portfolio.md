# Documentation de l'Architecture - Portfolio Tylden Hounsa

Ce document détaille l'architecture complète du fichier `index.html`. Il répertorie la structure sémantique, les classes CSS utilisées pour le style et les comportements (animations/JS), ainsi que l'organisation du contenu.

## 1. Méta-informations & Dépendances (Balise `<head>`)

- **Langue** : Français (`lang="fr"`)
- **Encodage** : UTF-8
- **Viewport** : Responsive standard (`width=device-width, initial-scale=1.0`)
- **Titre** : Tylden Hounsa — Data Analyst & Engineer
- **Polices (Google Fonts)** :
  - `Space Mono` (Styles: Italic, Regular, Bold) -> Souvent utilisé pour le code ou les éléments techniques (comme le terminal).
  - `Syne` (Styles: Regular, Semi-Bold, Bold, Extra-Bold) -> Utilisé pour les titres et le texte global.
- **Feuille de style CSS** : `.\assets\css\style.css`

---

## 2. Décorations Globales (`<body>`)

- `.glow-tr` : Effet de lueur (glow) positionné en haut à droite (Top-Right).
- `.glow-bl` : Effet de lueur positionné en bas à gauche (Bottom-Left).
*Comportement visuel probable* : Éléments en `position: absolute` ou `fixed` avec des filtres `blur` et des couleurs douces en arrière-plan pour donner un aspect moderne au fond.

---

## 3. Barre de Navigation (`<nav>`)

- **Conteneur parent** : `<nav>` (balise sémantique)
- **Logo** : `.nav-logo` (Texte stylisé `[ashborn539]`)
- **Liens** : `.nav-links` -> Contient des ancres (`<a>`) pointant vers les différentes sections (`#about`, `#skills`, `#projects`, `#roadmap`, `#contact`).

---

## 4. Section Hero (`#hero`)

La section d'introduction, scindée en deux parties visuelles (Texte + Terminal).

### Comportement Global
- **Animations d'entrée** : Les classes `.fade-in` combinées à `.fade-in-X` (1 à 5, et `terminal`) suggèrent une animation d'opacité/translation déclenchée au chargement (en CSS) ou via JS, avec des délais échelonnés (staggered animation).

### Partie Gauche : Textes & Boutons
- `.hero-badge` : Étiquette (badge) avec un point décoratif `.hero-badge-dot`.
- `.hero-h1` : Titre principal avec un point stylisé séparé `.dot`.
- `.hero-sub` : Sous-titre détaillant la filière, incluant une flèche décorative `.arrow`.
- `.hero-desc` : Paragraphe descriptif principal.
- `.hero-btns` : Conteneur pour les boutons d'appel à l'action.
  - `.btn-primary` : Bouton principal ("Voir mes projets").
  - `.btn-secondary` : Bouton secondaire ("Me contacter").

### Partie Droite : Terminal UI Mockup (`.terminal`)
Interface simulant une console de commande.
- `.terminal-bar` : Barre supérieure (barre de titre macOS-like).
  - Points de contrôle : `.dot-red`, `.dot-yellow`, `.dot-green`.
  - Titre : `.terminal-label`.
- `.terminal-body` : Fenêtre de texte.
  - `.prompt` : Symbole `$` pour imiter la ligne de commande.
  - `.cmd` : La commande tapée (`whoami`, `cat skills.txt`, `echo $OBJECTIVE`, `./run_portfolio.sh`).
  - `.out` : La réponse du terminal.
  - `.cursor` : Tiret du bas `_` simulant un curseur clignotant.

---

## 5. Composants Communs / Réutilisables
Plusieurs éléments se retrouvent dans les sections suivantes :
- `.container` : Conteneur principal pour limiter la largeur et centrer le contenu.
- `.section-header` : Entête de section standard.
  - `.section-num` : Numérotation (01, 02...).
  - `<h2>` : Titre de la section.
  - `.section-divider` : Ligne séparatrice stylisée.
- `.reveal` : Classe utilisée massivement sur les conteneurs des sections pour gérer une **animation d'apparition au scroll** (IntersectionObserver probablement géré par `script.js`).

---

## 6. Section À propos (`#about`)

- `.about-grid` : Grille principale (probablement `display: grid` à 2 colonnes).
- **Colonne 1 : Présentation (`.about-text`)**
  - `.hl` (Highlight) : Mise en évidence de mots clés (MIASHS, Data Analyst...).
  - `.stats` : Conteneur des blocs statistiques.
    - `.stat-num` : Chiffre important (4, 5+, 2).
    - `.stat-label` : Description de la stat.
- **Colonne 2 : Fiche d'informations (`.info-card`)**
  - `.info-row` : Ligne contenant un icône et une info.
    - `.info-icon` : Émoji illustratif.
    - `.info-label` : Titre de l'info (Email, Objectif...).
    - `.info-value` : Valeur.
  - `.btn-cv` : Bouton de téléchargement de fichier (pointe vers le pdf du CV).

---

## 7. Section Compétences (`#skills`)

- `.skills-grid` : Grille regroupant plusieurs catégories de compétences.
- `.skill-card` : Carte de catégorie (Langages, Analyse, ML...).
  - **Lignes de compétences** : `.skill-row` (regroupe le nom et le niveau).
    - `.skill-name` : Technologie.
    - `.skill-level` : Niveau (Notions, Intermédiaire...).
  - **Badges d'outils** : `.tools-wrap` (Conteneur de type flex/wrap).
    - `.tool-badge` : Élément type bulle de mot clé (Git, VS Code...).

---

## 8. Section Projets (`#projects`)

- `.projects-grid` : Grille d'affichage des projets.
- `.project-card` : Carte d'un projet individuel. La classe `.featured` est appliquée au premier pour le mettre en avant (probablement plus grand).
  - **Entête de la carte** : `.project-top`.
    - `.project-tag` : Catégorie ou langages principaux.
    - `.project-year` : Année.
  - `.project-num` : Numérotation du projet en grand fond (01, 02).
  - `.project-title` : Titre du projet.
  - `.project-desc` : Description.
  - **Points clés** : `.project-highlights` (liste de 3 éléments descriptifs).
  - **Technologies (Stack)** : `.project-stack`.
    - `.stack-badge` : Petit mot-clé technique (Python, Java...).
  - `.project-link` : Lien sortant vers GitHub (`target="_blank"`, `rel="noopener noreferrer"` pour la sécurité).

---

## 9. Section Roadmap (`#roadmap`)

- `.roadmap-intro` : Phrase d'introduction simple.
- `.roadmap-list` : Conteneur de la ligne du temps (timeline).
- `.roadmap-item` : Chaque étape de la roadmap.
  - `.roadmap-dot` : Le marqueur sur la timeline (point, case cochée, flèche).
  - `.roadmap-content` : Contenu texte de l'étape.

### Modificateurs d'état (Roadmap)
Ces classes appliquent des styles spécifiques en fonction de la progression :
- `.done` : Étape terminée (vert ou couleur de validation, opacité pleine).
- `.current` : Étape en cours (couleur d'accentuation principale).
- `.upcoming` : Étape future (gris, opacité réduite).

---

## 10. Section Contact (`#contact`)

- `.contact-grid` : Grille à 2 colonnes (Informations à gauche, Formulaire à droite).
- **Colonne Gauche (Infos)**
  - `.contact-intro` : Paragraphe d'appel à l'interaction.
  - `.contact-links` : Conteneur des moyens de contact.
  - `.contact-link` : Lien cliquable (Mail, LinkedIn, GitHub).
    - `.contact-link-icon` : Symbole ou lettre de logo.
    - `.contact-link-label` & `.contact-link-value` : Titre et ID du compte.
- **Colonne Droite (Formulaire)**
  - `.form` : Div englobant le pseudo-formulaire.
  - `.form-group` : Regroupe un `label` et un `input` ou `textarea`.
  - `.btn-send` : Bouton de validation (note : c'est un `<button type="button">`, le comportement d'envoi nécessitera d'être codé en JS car ce n'est pas une balise `<form>`).

---

## 11. Pied de Page (`<footer>`)

- `.footer-inner` : Conteneur interne avec du padding.
- `.footer-logo` : Rappel de `[ashborn539]`.
- `.footer-copy` : Copyright et mention.
- `.footer-links` : Liens sortants de bas de page (GitHub, LinkedIn).

---

## 12. Script (JS)

- **Source** : `.\assets\js\script.js` (Inclus juste avant la fermeture de `</body>` pour ne pas bloquer le rendu du DOM).
- **Comportements attendus (Déduits des classes HTML)** :
  1. **Reveal on Scroll** : Ciblage de tous les éléments ayant la classe `.reveal` via `IntersectionObserver` pour ajouter une classe `.active` ou `.visible` quand l'élément entre dans le viewport.
  2. **Animations au chargement** : Lancement conditionnel ou séquentiel des `.fade-in`.
  3. **Curseur clignotant** : Possible script pour animer le `.cursor` du terminal.
  4. **Smooth Scroll** : Gestion des liens de la `<nav>` (`a[href^="#"]`) pour glisser en douceur vers la section appropriée.
  5. **Validation Formulaire** : Le bouton `.btn-send` nécessitera un script pour récolter les données et les envoyer ou afficher un message.
