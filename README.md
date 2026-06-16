# ComfyUI Prompt Studio — plugin Obsidian

Une interface moderne pour organiser tes **prompts, idées, styles, personnages et modèles** ComfyUI, avec **import d'images + métadonnées depuis CivitAI** et d'autres sources.

Chaque entrée est une simple note markdown dans ton coffre : tu gardes la portabilité d'Obsidian (recherche, liens, sync, sauvegarde) avec une UI dédiée par-dessus.

---

## Installation (aucune compilation nécessaire)

1. Dans ton coffre Obsidian, ouvre le dossier caché `.obsidian/plugins/`
   (s'il n'existe pas, crée-le).
2. Copie **tout le dossier `comfy-prompt-studio`** dedans. Tu dois obtenir :
   ```
   <ton-coffre>/.obsidian/plugins/comfy-prompt-studio/manifest.json
   <ton-coffre>/.obsidian/plugins/comfy-prompt-studio/main.js
   <ton-coffre>/.obsidian/plugins/comfy-prompt-studio/styles.css
   ```
3. Dans Obsidian : **Paramètres → Plugins tiers** → désactive le mode restreint si besoin,
   puis clique sur **Recharger les plugins** (icône 🔄).
4. Active **ComfyUI Prompt Studio** dans la liste.
5. Clique sur l'icône baguette magique 🪄 dans la barre latérale, ou lance la commande
   **« Ouvrir Prompt Studio »** (palette de commandes, `Ctrl/Cmd + P`).

> Le plugin est marqué « desktop only » car il utilise les requêtes réseau et l'écriture
> de fichiers binaires (téléchargement d'images).

> Le `main.js` distribué est un **bundle généré**. Pour modifier le plugin, édite les
> sources dans `src/` puis recompile (voir *Développement* en bas).

---

## Fonctionnalités

**Import par lien CivitAI ⚡ (nouveau)**
- Bouton **« Depuis un lien »** (ou commande *Importer depuis un lien CivitAI*) :
  colle l'URL d'une **image**, d'un **modèle** ou d'un **post** CivitAI → une entrée
  est créée automatiquement.
- Le prompt positif/négatif, le modèle (checkpoint), les **LoRAs**, le sampler, les
  steps/CFG/seed/taille et l'image sont récupérés directement, **même quand l'API REST
  publique masque les métadonnées** (le plugin lit les vraies données de génération).
- Option *Vérifier dans l'éditeur avant d'enregistrer* si tu veux relire/ajuster.

**Bibliothèque**
- **Dossiers** : barre latérale arborescente — créer / renommer / supprimer, **glisser-déposer**
  des entrées d'un dossier à l'autre, compteurs par dossier, filtrage (avec ou sans sous-dossiers).
- **3 modes d'affichage** : **Grille**, **Liste** (compacte) et **Mosaïque** (façon Pinterest),
  avec **curseur de taille** des cartes — pratique quand la bibliothèque est volumineuse.
  Le mode et la taille sont **mémorisés**.
- Filtres par type (avec compteurs) et par tag, **favoris** (★) et **tri** (récent / modifié / titre / modèle).
- Recherche plein texte (titre, prompts, modèle, sampler, tags, LoRAs) + compteur de résultats.
- **Multi-sélection** + actions groupées : favori, déplacer, taguer, supprimer en masse.
- **Menu clic-droit** par entrée : copier le prompt / le négatif / le **format A1111**, favori,
  **dupliquer**, déplacer, ouvrir la note, ouvrir la source, supprimer.
- **Visionneuse plein écran** (clic sur une image) avec navigation au clavier (← →, Échap).
- **Statistiques** et **export JSON** de toute la bibliothèque (menu ⋯).
- Éditeur complet : type, prompt positif/négatif, modèle, sampler, steps, CFG, seed, taille,
  LoRAs, tags, **dossier**, source, notes, galerie d'images.

**Navigateur CivitAI**
- Onglet *Images* : recherche **par artiste / pseudo** (récupère tout son catalogue, pas
  seulement les récents), **source** (Tout CivitAI / **Mes follows**), tri (récent / réactions /
  commentaires), **filtre par date** (Tout le temps / Année / Mois / Semaine / Jour) et
  **sélecteur de contenu inline** (SFW / Soft / Mature / X / **Tout NSFW**) —
  indispensable car beaucoup d'artistes ne publient que de l'adulte.
- **Vidéos & GIF** : lecture animée dans les cartes, l'aperçu et la visionneuse, badge ▶,
  et téléchargement local (`.mp4` / `.webm` / `.gif`, embarqués comme média dans la note.
  *« Mes follows » nécessite ta clé API CivitAI.*
- Onglet *Modèles* : recherche par **nom**, **tag / style** (ex. *anime*, *realistic*) et
  **type** (Checkpoint / LoRA / Embedding / ControlNet / VAE…), tri, import direct.
- **Défilement infini** + bouton « Charger plus » (pagination par curseur), badges de
  réactions/téléchargements, bouton **« Ouvrir sur CivitAI »**.
- Clique une image → aperçu qui **charge le vrai prompt/négatif/LoRAs** à la demande →
  **« Importer dans la bibliothèque »** crée l'entrée et télécharge l'image en local.

**Import de métadonnées d'image (autres plateformes / local)**
- Commande **« Importer les métadonnées d'une image PNG du coffre »** : lit les blocs
  texte PNG embarqués (format Automatic1111 `parameters` et workflow ComfyUI `prompt`)
  et crée une entrée pré-remplie. Pratique pour les PNG exportés par ComfyUI/A1111.

---

## Réglages (Paramètres → ComfyUI Prompt Studio)

- **Dossier de la bibliothèque** : où sont stockées les notes (défaut `ComfyUI Prompt Studio`).
- **Sous-dossier des images** : où sont copiées les images importées.
- **Télécharger les images en local** : sinon, seule l'URL distante est conservée.
- **Vue par défaut** : Grille / Liste / Mosaïque.
- **Inclure les sous-dossiers** : afficher aussi les entrées des sous-dossiers du dossier sélectionné.
- **URL de base de l'API CivitAI** : `https://civitai.com` par défaut.
  Tu peux pointer vers un **miroir compatible** (ex. `https://civitai.red`) ou une autre instance —
  le plugin tape l'endpoint `/api/v1/...` sur cette base.
- **Clé API CivitAI** : optionnelle, mais recommandée. Certains contenus et des quotas de
  requêtes plus élevés la nécessitent. Crée-la dans tes paramètres de compte CivitAI.
- **Filtre de contenu** : `None` (SFW, par défaut) → `Soft` / `Mature` / `X`.
  Les niveaux adultes peuvent exiger une clé API.

---

## Format des notes

Chaque entrée ressemble à :

```markdown
---
cps-type: "prompt"
model: "SDXL"
sampler: "DPM++ 2M Karras"
steps: 30
cfg: 6
seed: 123456
size: "832x1216"
loras:
  - "detail-tweaker"
tags:
  - "cyberpunk"
  - "portrait"
images:
  - "ComfyUI Prompt Studio/attachments/portrait.png"
source: "https://civitai.com/images/..."
created: "2026-06-06T..."
---
# Portrait cyberpunk néon

## Positive
masterpiece, best quality, ...

## Negative
lowres, bad anatomy, ...

## Notes
...
```

Tu peux éditer ces notes à la main : le plugin les relit automatiquement.

---

## Aller plus loin

Pistes d'évolution : intégration directe avec une instance **ComfyUI** (envoi de prompt /
file d'attente), prévisualisation du workflow ComfyUI, autocomplétion de tags depuis une
base Danbooru/e621 complète, et synchronisation multi-appareils des snippets.

---

## Nouveautés 1.5

- **i18n** : interface FR / EN (réglage *Langue*).
- **Snippets de prompt** réutilisables + **wildcards** `{a|b|c}` résolus à la copie.
- **Autocomplétion de tags** et **pondération** `(tag:1.1)` (Ctrl/Cmd + ↑/↓ dans les champs de prompt).
- **Import enrichi** : sélecteur de fichier, import par lot d'un dossier, toutes les images d'un post CivitAI, métadonnées PNG/JPEG/WebP.
- **Gestion d'images** dans l'éditeur (ajout / réordonnancement / couverture / retrait).
- **Notes (étoiles)** + tri par note, **recherches enregistrées** (collections dans la barre latérale).
- **Performances** : miniatures CivitAI redimensionnées, vidéos hors écran mises en pause.
- **Accessibilité** : navigation clavier des cartes (← → Entrée Suppr), focus visibles, barre d'outils collante, squelettes de chargement.

---

## Développement (build)

Le plugin est écrit en **TypeScript** et compilé avec **esbuild**.

```bash
npm install      # dépendances de dev
npm run build    # génère main.js (bundle de production)
npm run dev      # mode watch (recompile à chaque modif)
npm test         # build + tests (node:test : logique + DOM via jsdom)
npm run lint     # ESLint
```

- Sources modulaires dans `src/` : `types`, `constants`, `i18n`, `utils`, `metadata`, `civitai`, `dom`, `store`, `ui`, `main` (graphe de dépendances sans cycle).
- Sortie : `main.js` (bundle, ne pas éditer à la main).
- `manifest.json`, `versions.json`, `styles.css` sont livrés tels quels.
- `npm run typecheck` doit rester vert (0 erreur).
