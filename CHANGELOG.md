# Changelog

## 1.18.0 — Prompt Builder repensé
- **Refonte complète du Prompt Builder** : grand modal pleine largeur, disposition pro en deux colonnes (blocs à gauche, aperçu collant à droite).
- **Chips cliquables par bloc** : chaque bloc (Sujet, Style, Ambiance, Lumière, Caméra, Optique, Composition, Rendu) propose ses valeurs canoniques en pastilles à activer/désactiver d'un clic, en plus de la saisie libre avec autocomplétion.
- **Nouveaux blocs** : section **Qualité** (boosters masterpiece/8k/sharp focus…) et **Negative Prompt** avec presets courants (lowres, bad anatomy, watermark…).
- **Pondération par bloc** via un contrôle compact `[−] ×1.0 [+]` (clic sur la valeur = reset).
- **Aperçu live amélioré** : positif et négatif séparés, copie indépendante de chacun, compteur de segments/caractères.
- **Plus complet** : choix du type d'entrée (Prompt/Idée/Style/Personnage), dossier de destination, et bouton **Réinitialiser**.

## 1.17.6 — Le dossier actif ne se réinitialise plus
- **Filtrer par type ne te sort plus du dossier** : cliquer sur Prompts / Idées / Styles… conserve le dossier actif et filtre à l'intérieur — même si la section est vide pour ce dossier (plus de bascule surprise vers la racine).
- Le type reste surligné dans la barre latérale même quand un dossier est actif, et le **dossier actif garde son halo en permanence**. Le titre de colonne combine désormais dossier + type (ex. « MonDossier · Prompts »).

## 1.17.5 — Sélecteur de dossier & nettoyage
- **Bouton de dossier dans la barre du haut** : affiche en permanence le dossier actif (« Toutes », « Racine » ou le nom du dossier) et permet d'en changer **sans quitter l'onglet courant** — pratique pour choisir la destination des imports CivitAI à la volée.
- **Dossier actif « glowing »** : dans la barre latérale, le dossier sélectionné est mis en valeur par un halo accent ; les autres restent neutres.
- **Snippets retirés** : la fonctionnalité de snippets de prompt (réglages, éditeur, moodboard, menus) est supprimée — interface allégée.

## 1.17.4 — Dossiers & sélection multiple
- **Scroll préservé en multi-sélection** : cocher/décocher une entrée ne reconstruit plus toute la liste. Fini le retour brutal en haut quand on sélectionne une nouvelle entrée parmi des centaines.
- **« Racine » toujours visible** dans la section Dossiers : un nœud racine permanent (cliquable, cible de dépôt et destination d'import), même sans sous-dossier.
- **Dossier courant toujours indiqué** : le dossier actif reste surligné dans la barre latérale quel que soit l'onglet, et l'onglet CivitAI affiche désormais « Import → <dossier> » pour montrer où atterriront les imports.

## 1.17.3 — Sidebar harmonisée
- La barre latérale gauche adopte le **même fond** que le reste de l'interface (`--background-primary`) au lieu d'un gris plus clair. Seul un fin filet de 1px la sépare désormais (style plat), et la coupure visible en bas disparaît.

## 1.17.2 — Catégorie par défaut des imports CivitAI Images
- Nouveau réglage **« Type des imports CivitAI Images »** (section CivitAI) : choisis la catégorie attribuée par défaut aux entrées créées depuis l'onglet CivitAI Images — **Prompt** (défaut), **Idée**, **Style** ou **Personnage**. Les imports de modèles restent en « Modèle ».

## 1.17.1 — CivitAI plus résistant aux 503
- **Réessais renforcés** sur les erreurs serveur CivitAI (503/500/502) et 429 : de 3 à **6 tentatives** avec backoff exponentiel + jitter, et respect de l'en-tête `Retry-After` quand CivitAI l'envoie (plafonné à 15 s). Les erreurs réseau/transport sont désormais réessayées elles aussi.
- **Relance automatique de la pagination** : si une page suivante échoue malgré tout (défilement infini), le plugin retente **2 fois** tout seul avec un compte à rebours visible (3 s) avant d'afficher le bouton « Charger plus ». Plus besoin de cliquer pour la plupart des 503 passagers.

## 1.17.0 — Retrait de l'IA (allègement)
- **Toute la couche IA est retirée** : moteur Claude/OpenAI, embeddings (API et locaux MiniLM/CLIP), gestion/téléchargement de modèles, analyse d'image, Reverse Engine, recherche naturelle et recherche par image. Réglages nettoyés (plus de section « Intelligence »), bundle allégé (~−20 ko), 3 modules supprimés (`intelligence`, `embeddings`, `localEmbed`).
- **Conservé (100 % local, sans IA)** : Smart Tags (auto-facettes depuis le prompt), Style DNA, tri **« Similaires »** lexical, et **« Pour toi »** (classement CivitAI selon ton Style DNA). La commande « Analyser toute la bibliothèque » reste (ré-enrichissement local).

## 1.16.2 — Correctif canvas (clic droit / ctrl+clic)
- Le clic droit (ou ctrl+clic sur Mac) sur un élément du canvas ne démarre plus un glisser. Corrige le bug où, après « Extraire la palette » (menu contextuel), l'image se retrouvait sélectionnée et collée au curseur. Le glisser, le pan du fond et le redimensionnement ne réagissent qu'au **bouton gauche**.

## 1.16.1 — Ajustements UX
- Panneau de détail : l'onglet **« Détails »** seul (inutile) n'apparaît plus ; la barre d'onglets ne s'affiche que s'il y a des **Notes**.
- **Import CivitAI à la chaîne** : importer une image/un modèle ne te ramène plus à l'Accueil — tu restes dans le navigateur CivitAI et peux enchaîner. Le bouton d'import passe au **✓ vert** une fois ajouté.
- **Canvas** : un simple clic gauche ne déplace plus l'élément (seuil de 4 px) — seul un vrai glisser le bouge.

## 1.16.0 — Refonte UI « plate » (Notion-like)
- **Layout sur un seul plan** : fini les panneaux « flottants » (cartes arrondies + ombres + espaces). Sidebar, liste et panneau de détail sont désormais séparés par de simples filets 1 px, collés bord à bord — **plus de place utile** et look Notion.
- **Cartes plates** : bordure fine, sans ombre, coins plus discrets (8 px), survol calme (fond/bordure au lieu de soulèvement + zoom). Grille plus dense (gap réduit).
- **Vue liste façon Notion** : lignes sans carte, séparées par un filet, surbrillance au survol, plus compactes.
- **Panneau de détail repensé** : intégré (bordure gauche, fond identique au contenu), en-tête à boutons fantômes (fermer à gauche, actions à droite), sections aérées et à plat, blocs de prompt allégés.
- Boutons/icône de marque aplatis (accent uni, sans dégradé ni ombre) ; barre du haut un peu plus basse.

## 1.15.0 — Recherche par image CLIP, index incrémental, indexation fluide, fix 500
- **Recherche CivitAI par image avec CLIP** : sur l'onglet Images, le bouton **Image** classe les résultats par **proximité visuelle réelle** à ton image (embeddings CLIP des vignettes + cosinus). Repli sur le moteur IA (LLM → modèles) si CLIP indisponible ou sur l'onglet Modèles. (Selon la CORS du CDN CivitAI, l'analyse des vignettes peut échouer — message clair dans ce cas.)
- **Index sémantique incrémental** : créer / modifier / supprimer une entrée met à jour l'index automatiquement (réindexation sérialisée + sauvegarde différée), tant qu'un index a déjà été construit. Plus besoin de tout reconstruire à la main.
- **Indexation non-bloquante** : micro-pauses entre lots/images pour que l'UI reste fluide pendant la construction (utile en local mono-thread WASM).
- **Correctif CivitAI 500** : un bouton **« Réessayer »** s'affiche désormais aussi au premier chargement (pas seulement en scroll), car les erreurs 500 par pseudo sont souvent intermittentes.

## 1.14.0 — Images similaires (CLIP)
- **Index d'images CLIP** : quand le mode local est `CLIP` ou `Les deux`, la commande « Construire l'index sémantique » calcule aussi un **vecteur visuel** par image de couverture (sidecar étendu `{ text, images }`, rétro-compatible avec l'ancien format texte seul).
- **Section « Images similaires »** dans le panneau de détail : entrées visuellement proches (cosinus sur les vecteurs CLIP), distincte de « Similaires » (texte). 100 % local.

## 1.13.3 — Embeddings locaux : contournement détection Node (Electron)
- Masque temporairement `process` pendant le chargement des modèles. Sous Electron/Obsidian, `process.versions.node` fait croire à onnxruntime qu'il tourne dans Node.js, donc il importe le module Node « worker_threads » → backend WASM introuvable. En se faisant passer pour un navigateur, onnxruntime utilise les Web Workers. `process` est restauré juste après.

## 1.13.2 — Embeddings locaux : CDN esm.sh + source configurable
- Bascule le chargement de transformers.js sur **esm.sh** (au lieu de jsdelivr `+esm`) : esm.sh fournit des shims navigateur pour les builtins Node, ce qui résout définitivement l'erreur « Failed to resolve module specifier 'worker_threads' ».
- **CDN configurable** dans les réglages (« Source des modèles ») : si un CDN échoue, on peut en essayer un autre sans rebuild.

## 1.13.1 — Correctif embeddings locaux (WASM)
- Force le backend WASM d'onnxruntime en **mono-thread sans worker/proxy** (`numThreads = 1`, `proxy = false`). Corrige l'erreur « no available backend found / Failed to resolve module specifier 'worker_threads' » sous Electron/Obsidian.

## 1.13.0 — Embeddings locaux (expérimental) : MiniLM / CLIP
- **Embeddings 100 % locaux** (`localEmbed.ts`, via transformers.js chargé en lazy depuis un CDN) : réglage **MiniLM (texte)** / **CLIP (texte + image)** / **Les deux**, sans clé ni API, hors-ligne. Alimente la recherche sémantique « Similaires ».
- **Gestion des modèles depuis les réglages** : statut (téléchargé / non), bouton **Télécharger** (avec progression) et **Supprimer** (vide le cache) pour chaque modèle — pour libérer l'espace si tu n'utilises plus l'IA.
- Intégré à la commande « Construire l'index sémantique » (utilise le local quand activé, sinon l'API).
- ⚠️ **Expérimental** : le téléchargement du modèle (~25–90 Mo) et l'exécution WASM peuvent être bloqués par la sécurité (CSP) d'Obsidian ; échec propre avec message dans ce cas. L'option API reste disponible et fiable.

## 1.12.1 — Correctif scroll CivitAI
- **Navigateur CivitAI** : corrige le blocage « CivitAI a répondu 500 » lors du défilement infini (fréquent sur la pagination par pseudo). Le client réessaie désormais les erreurs serveur 5xx (et 429) avec backoff ; et quand une page suivante échoue durablement, le défilement auto s'arrête proprement et propose un bouton **« Charger plus »** au lieu de redemander la page fautive en boucle.

## 1.12.0 — Connecteurs moodboard, embeddings neuronaux, recherche par image
- **Connecteurs / flèches dans le moodboard** : bouton **Connecter** (mode), clic sur deux éléments pour tracer une flèche ; couche SVG qui suit le pan/zoom et le déplacement/redimensionnement en direct ; suppression d'une flèche au clic ; nettoyage automatique quand un élément est supprimé.
- **Embeddings neuronaux** (`embeddings.ts`) : index sémantique via un endpoint **compatible OpenAI** (`/embeddings` — OpenAI `text-embedding-3-*`, ou serveurs locaux Ollama/LM Studio avec `nomic-embed-text`…). Commande **« Construire l'index sémantique »** (+ menu `…`), persisté en sidecar JSON du plugin, chargé au démarrage. La section **« Similaires »** fusionne désormais **lexical + neuronal** (0,45 / 0,55) quand l'index est prêt — sinon reste 100 % lexical.
- **Recherche CivitAI par image** : bouton **Image** dans le navigateur → une image du coffre est analysée (IA vision) puis convertie en recherche de modèles (style/sujet/modèle détectés). Repose sur le moteur IA configuré.

## 1.11.0 — Phase 4 : Prompt Stack & Canvas Intelligence
- **Prompt Stack** : nouveau type d'entrée **Stack** (`cps-type: stack`) qui agrège Prompt + Négatif + LoRAs + Modèle + **Workflow** (lien `.json`/`.canvas`) + **images de référence**. L'éditeur expose un champ Workflow (avec sélecteur de fichier) et un gestionnaire d'images de référence ; le panneau de détail affiche le workflow (ouvrable) et la bande de références. Commande **« Nouvelle Prompt Stack »**.
- **Canvas Intelligence** (`canvas.ts`) : génère un fichier **`.canvas` natif Obsidian** (JSONCanvas) depuis tes entrées — un nœud-fichier par note, **regroupées par modèle**, colorées par type, et **reliées** quand elles partagent un LoRA. Re-générable. Accessible via la commande « Exporter la bibliothèque vers un Canvas », le menu `…` (« Exporter la vue vers un Canvas ») et la barre de sélection (bouton **Canvas**). Le fichier s'ouvre directement dans le Canvas d'Obsidian.

## 1.10.0 — IA (Phase 3) : moteur configurable Claude / autre / local
- **Choix du moteur IA dans les réglages** (`intelligence.ts`) : **Local** (aucune IA, heuristiques), **Claude** (API Anthropic, vision — modèle par défaut `claude-opus-4-8`, configurable), ou **Autre IA compatible OpenAI** (URL + clé + modèle ; OpenAI, Ollama, LM Studio…). Tout passe par `requestUrl` (Obsidian), avec repli local automatique.
- **Style Intelligence** : action **« Analyser l'image (IA) »** (menu d'une entrée / panneau) → résumé, facettes, prompt de reproduction, modèle probable et tags, fusionnés dans l'entrée. L'image est réduite localement (≤ 1024 px) avant envoi.
- **Reverse Engine** : commande **« Reverse : créer une entrée depuis une image (IA) »** → lit d'abord les métadonnées EXIF/PNG, sinon estime via l'IA, puis crée une entrée avec tags, facettes et **backlinks** `[[…]]` vers les entrées similaires.
- **Recherche CivitAI en langage naturel** : bouton **« IA »** dans le navigateur → convertit une requête libre (« portrait cyberpunk sombre, style anime ») en filtres (tag, type, tri, période…), avec repli local par mots-clés.

## 1.9.0 — Socle « intelligence » (Phase 1, 100 % local)
- **Taxonomy** (`taxonomy.ts`) : vocabulaire contrôlé sur 8 axes (subject, style, mood, lighting, camera, lens, composition, rendering) avec valeurs canoniques + synonymes, classification locale d'un prompt en facettes, et calcul du **Style DNA**.
- **Schéma de frontmatter étendu** : facettes structurées (`style:`, `lighting:`, `camera:`…) + `style_dna:` + `blocks:`, le tout aplati dans `tags:` pour rester compatible avec la recherche et le volet de tags natifs d'Obsidian. Le parseur frontmatter maison gère désormais les **objets imbriqués** (testé, sans régression).
- **Prompt Builder** (`prompt-builder.ts`) : construction d'un prompt par **blocs** (Subject, Style, Mood, Lighting, Camera, Lens, Details, Negative) avec pondération par bloc, autocomplétion depuis la taxonomy, aperçu live, et enregistrement comme entrée. Accessible via la sidebar **Outils** et la commande « Prompt Builder ».
- **Smart Tags (local)** : à la création d'une entrée (y compris imports CivitAI), les facettes sont déduites du prompt et ajoutées aux tags. Réglable (Activé local / Désactivé).
- **Style DNA** (`style-dna.ts`) : profil stylistique pondéré d'un dossier ou de toute la bibliothèque — graphe en barres, style dominant, recommandations d'axes à explorer.
- Sidebar : nouvelle section **Outils** (Prompt Builder, Style DNA).
- **Commande « Analyser toute la bibliothèque »** (et menu `…`) : ré-enrichit les notes existantes en place (facettes + tags + Style DNA), avec barre de progression.
- **Moteur de similarité local** (`similarity.ts`, Phase 2) : vecteurs creux pondérés (facettes, tags, modèle, LoRAs, tokens du prompt) + cosinus ; section **« Similaires »** dans le panneau de détail (top 5, cliquable, score %). Architecture prête pour brancher des embeddings neuronaux plus tard.
- **Recherche CivitAI améliorée** (Phase 2, sans IA) : **cache mémoire** des réponses (TTL 5 min — recherches répétées instantanées, moins de 429) ; tri **« Pour toi »** des images selon ton **Style DNA** + modèles fréquents (`civitai-rank.ts`) ; **autocomplétion taxonomy** sur la recherche de modèles par tag ; action **« Chercher sur CivitAI »** depuis le menu d'une entrée (ouvre l'onglet Modèles sur son modèle).
- **Classification de facettes plus fiable** : `facetsFromText` reconnaît désormais les valeurs/synonymes même au sein d'un segment multi-mots (matchers précompilés à frontières de mots) — améliore Smart Tags et le tri « Pour toi ».

## 1.8.0
- **Suppression en cascade** : supprimer une entrée (ou plusieurs en lot) met aussi à la corbeille les images/fichiers locaux qu'elle référence — sauf si une autre entrée s'en sert encore. Tout reste récupérable via la corbeille.
- **Structure de fichiers clarifiée** : le monolithe `ui.ts` (1867 lignes) est éclaté en `view.ts` (vue principale), `modals.ts` (toutes les fenêtres) et `settings.ts` (réglages). En-têtes et bannières de commentaires obsolètes nettoyés dans tout `src/`.
- **Code simplifié** : virtualisation par fenêtrage retirée au profit d'un rendu progressif unique ; helpers de modale (`copyBlock`, `factGrid`, `cloneDraft`) factorisés ; ombrage de la variable `t` dans les réglages corrigé.
- **UI remodelée (layout 3 colonnes)** : barre du haut avec recherche centrée, sidebar structurée par sections (Accueil · Bibliothèque par type · CivitAI · **Inspiration : Moodboards & Références** · Dossiers · Collections), liste centrale enrichie (miniature, tags inline, méta « Modèle · N LoRAs · Workflow », note et temps relatif) et **panneau de détail intégré à droite** qui remplace la modale (aperçu, onglets Détails/Notes, specs, LoRAs avec poids, actions).
- **Tout en coins arrondis** : couche de tokens de design, panneaux structurels en cartes arrondies « flottantes », survols animés et zoom des miniatures, entrée animée des cartes, micro-interactions sur chips/boutons/étoiles, lightbox soignée. Respecte `prefers-reduced-motion`. Responsive : panneau en tiroir et sidebar masquée sur vue étroite.
- **Moodboards = galerie + canvas de réflexion libre** (nouveau module `moodboard.ts`). **Galerie** : aperçu de tous les boards (miniatures), créer / ouvrir / renommer / dupliquer / supprimer. **Canvas** : pan/zoom (molette + boutons + « tout afficher »), 4 types d'éléments — **images** du coffre, **notes adhésives** colorées, **textes** libres, **nuances de couleur**. Glisser/redimensionner, dupliquer, avancer/reculer (z-index), légendes d'images, suppression au clavier, sauvegarde auto. **Menu enrichi** : retour galerie, renommer/dupliquer/vider le board, aimant à la grille, note depuis un snippet. La section « Références » a été retirée.
- **Bouton « Depuis un lien »** ajouté dans la barre du haut (import CivitAI direct), à côté de « Nouveau ».
- **Moodboard** : bouton **« Depuis la bibliothèque »** (ajouter l'image d'une entrée existante, avec sa légende) et **« Extraire la palette »** d'une image en nuances de couleur (clic droit).
- **Moodboard — multi-sélection & nouvelles fonctions** : **MAJ+clic** pour sélectionner plusieurs éléments, **MAJ+glisser** = lasso ; déplacement et suppression de groupe ; raccourcis **Ctrl/Cmd+A** (tout), **Ctrl/Cmd+D** (dupliquer la sélection), **flèches** (déplacer, +MAJ = ×10), **Échap** (désélectionner) ; menu **Aligner/répartir** (gauche/centre/droite/haut/bas) ; nouvel élément **Cadre / zone** (rectangle titré pour regrouper visuellement).
- **Dossier d'enregistrement des images** configurable (réglages) : par défaut sous la bibliothèque, ou n'importe quel dossier du coffre — **« / » pour la racine** d'Obsidian.

## 1.7.0
- **Refactorisation modulaire** : l'ancien `src/main.ts` monolithique (~3000 lignes) est découpé en modules à dépendances acycliques : `types`, `constants`, `i18n`, `utils`, `metadata`, `civitai`, `dom`, `store`, `ui`, `main`.
- **Typage** : `types.ts` (interfaces Settings/Entry/EntryDraft/Snippet/SavedSearch…), tous les champs de classe déclarés, signatures des modules feuilles typées. `npm run typecheck` passe à **0 erreur** avec des options strictes (`noImplicitThis`, `strictFunctionTypes`, `strictBindCallApply`, `alwaysStrict`).
  - `noImplicitAny`/`strictNullChecks` restent désactivés (passe de typage dédiée à venir) — documenté dans `tsconfig.json`.
- Aucune modification de comportement : annotations effacées au build, 20/20 tests verts.

## 1.6.1
- **Virtualisation réelle** (fenêtrage) au-delà de 400 entrées en vues Grille/Liste : seules les cartes visibles sont dans le DOM (tient à 10 000+), repli automatique sur le rendu progressif en cas d'erreur.
- **i18n complété** : réglages, menus, navigateur CivitAI, barre latérale, confirmations et notices traduits (FR/EN).
- **Édition des snippets** existants (en plus de l'ajout/suppression).
- **Tests DOM** (jsdom) en plus des tests de logique : `ratingStars`, `appendMedia` (img/vidéo/gif). Total : 20 tests.

## 1.6.0
- **Tests automatisés** (`npm test`, node:test) sur le parsing/metadata/CivitAI + exports de fonctions pures.
- **Parseur EXIF réel** pour JPEG (APP1) et WebP (RIFF) : lecture du UserComment (prompt A1111/ComfyUI), avec repli heuristique.
- **Autocomplétion enrichie** : lexique de ~200 tags booru + classement (préfixes d'abord).
- **Glisser-déposer** pour réordonner les images dans l'éditeur.
- **Rendu progressif** de la bibliothèque (lots de 80, chargement à l'approche du bas) pour les grandes collections.
- **Filtre par note** minimale (≥ N★) dans la barre d'outils.
- **i18n** étendu (éditeur, boutons, libellés) en plus de l'interface principale.
- `manifest.json` : champs `author` / `fundingUrl` ; `versions.json` ; gestion d'erreurs centralisée.

## 1.5.0
- **Architecture** : passage en TypeScript + build esbuild (`npm run build`). Le `main.js` livré est désormais un bundle généré ; les sources sont dans `src/`.
- **i18n** : interface FR / EN (réglage Langue, auto par défaut).
- **Snippets de prompt** : fragments réutilisables insérables dans l'éditeur ; wildcards `{a|b|c}` résolus à la copie.
- **Autocomplétion de tags** (lexique booru + tags du coffre) et **pondération** `(tag:1.1)` via Ctrl/Cmd + ↑/↓.
- **Import enrichi** : sélecteur de fichier, import par lot d'un dossier, import de toutes les images d'un post CivitAI, lecture des métadonnées PNG / JPEG / WebP.
- **Gestion d'images** dans l'éditeur : ajouter / réordonner / définir la couverture / retirer.
- **Notes (étoiles)** 1–5 + tri par note ; **recherches enregistrées** (collections).
- **Performances** : miniatures CivitAI redimensionnées, vidéos hors écran mises en pause.
- **UX/A11y** : barre d'outils collante, squelettes de chargement, navigation clavier des cartes, focus visibles.

## 1.4.0
- Filtre par date, source « Mes follows », support vidéo/GIF, espacement.

## 1.3.0
- Recherche CivitAI par artiste corrigée (période AllTime, NSFW), recherche modèles par tag/type, défilement infini.

## 1.2.0
- Dossiers, 3 modes d'affichage, taille ajustable, multi-sélection, menu contextuel, visionneuse, export JSON.

## 1.1.0
- Import par lien CivitAI (image / modèle / post) via les vraies données de génération.

## 1.0.0
- Version initiale : bibliothèque de prompts, navigateur CivitAI, import PNG.
