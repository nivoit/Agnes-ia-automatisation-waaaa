# 🎬 NewsReel Studio

> **Transformer l'actualité en un journal visuel généré par IA — satire, cinéma et engagement politique en 8 tableaux.**

[![Made with Love](https://img.shields.io/badge/Made%20with-%E2%9D%A4-red)](https://github.com)
[![Single File](https://img.shields.io/badge/Single%20File-100%25%20HTML-blue)]()
[![No Backend](https://img.shields.io/badge/Backend-Aucun-green)]()
[![Zero Build](https://img.shields.io/badge/Build-Aucun-orange)]()

---

## ✨ Ce qui rend ce code source fantastique

Ce projet tient dans **un seul fichier HTML de moins de 3000 lignes** et pourtant il fait ce que des plateformes entières tentent de faire avec des équipes de 20 personnes :

- **Recherche d'actualités réelles en direct** via une cascade intelligente de 3 APIs publiques gratuites (Free News API → Newsline → GDELT), sans clé, sans inscription, avec CORS ouvert. Le système **mémorise automatiquement** quel endpoint fonctionne le mieux et le rétrograde en cas d'échec (score `ok/(ok+fail)` persistant dans `localStorage`).

- **Analyse éditoriale profonde par IA** : au lieu de générer des images génériques, le modèle reçoit chaque actualité et la découpe en **8 scènes narratives distinctes** — la une, les décideurs, le citoyen lambda, les conséquences, les médias, une métaphore, un angle absurde, la conclusion. Les 8 légendes mises bout à bout forment un **véritable éditorial en 8 tableaux**.

- **Vision politique personnalisable** : l'utilisateur peut déclarer son orientation (raccourcis gauche/centre/droite/national/libertaire/communiste ou texte libre détaillé). L'IA garde les **faits exacts** mais colore **l'interprétation** dans ce sens — un vrai journaliste engagé, jamais haineux.

- **16 styles visuels pré-inclus** : Wes Anderson, Tim Burton, Bong Joon-ho, Tarantino + affiche punk, TikTok hook, affiche de cinéma, théâtre, BD franco-belge, New Yorker, Banksy, propagande soviétique, Aardman claymation, LEGO, manga, caricature Mad. **Chaque style est un simple prompt texte** — ajoutable en 5 secondes via l'interface.

- **Génération parallèle massive** : toutes les clés API Agnes saisies par l'utilisateur sont mises dans un **pool rotatif** avec gestion de cooldown 65s sur erreur 429 et détection de clé morte (3× 401/403). 16 workers consomment la queue en parallèle — 80 images générées en quelques minutes au lieu de plusieurs heures.

- **Édition d'image avancée** : une fois générée, chaque image peut être modifiée via 4 modes (Ajout de texte, Modification par IA, Insertion d'image, Fusion). Les modifications sont traitées par l'API d'image-to-image d'Agnes avec conservation du style visuel.

- **Diaporama vocal (TTS)** : génération d'un slideshow plein écran avec lecture des légendes via synthèse vocale (Puter.js, Voix native ou Google TTS). Interface de contrôle complète (play/pause, vitesse, mode silencieux).

- **Persistance IndexedDB intégrale** : sessions, images (en Blob), métadonnées, narrations, historique des éditions. Le bouton « Tout télécharger » reconstruit de vrais noms de fichiers (`newsreel_titre_v1_20261012_143022.jpg`) et déclenche 80 téléchargements en cascade avec barre de progression.

- **Zéro dépendance, zéro backend, zéro build**. Un `index.html`, un navigateur, c'est tout. On peut l'ouvrir depuis un téléphone en `file://` et il fonctionne.

- **Design sombre élégant** : palette or/noir, overlays plein écran avec progression réelle, confirmations inline (jamais de `confirm()` laid), boutons avec spinner intégré, animations douces.

---

## 🔧 Comment ça marche

### Vue d'ensemble du pipeline
