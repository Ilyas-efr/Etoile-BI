# Étoile BI

Un sketch p5.js adapté du projet "Dessins géométriques et artistiques" (v3ga). Ce dossier contient une version interactive qui utilise la librairie v3ga (`init_trace.js`) et permet d'exporter le dessin en PNG ou SVG.

**Contenu**
- `index.html` : page qui charge `p5.js`, la librairie v3ga et le sketch. Ajoute des boutons `Télécharger PNG` et `Télécharger SVG`.
- `sketch.js` : sketch p5 qui dessine l'`Étoile BI`. La fonction principale de rendu est `renderDessin(opts)` ; appelez `renderDessin({svg:true})` pour forcer le rendu SVG.
- `style.css` : styles basiques.

**Utilisation**
- Ouvrir `index.html` directement dans un navigateur peut fonctionner mais il est recommandé de servir le dossier depuis un petit serveur local (pour éviter des restrictions de CORS lors de conversion SVG→PNG).

Exemples (PowerShell / Windows) :

```powershell
# Avec Python 3 (dans le dossier contenant index.html)
python -m http.server 8000
# puis ouvrir http://localhost:8000

# Ou avec npm (si installé)
npx http-server -p 8000
```

- Cliquer sur `Télécharger PNG` pour obtenir une image raster (le bouton convertit automatiquement l'SVG en PNG si le sketch est rendu en SVG, sinon il utilise la sauvegarde du canvas).
- Cliquer sur `Télécharger SVG` pour télécharger le fichier vectoriel (si le sketch a déjà rendu un `<svg>`). Si aucun SVG n'existe, `renderDessin({svg:true})` sera appelé pour régénérer en SVG puis déclencher l'enregistrement.

**Rendu SVG / PNG**
- Le sketch expose `renderDessin(opts)` : passez `{svg:true}` pour initialiser le rendu en SVG via la librairie v3ga. Le code d'export prend en charge :
  - téléchargement direct du `<svg>` en `.svg` ;
  - conversion du `<svg>` en PNG via un canvas et téléchargement en `.png`.

**Utiliser la librairie v3ga en local (optionnel)**
Actuellement `index.html` charge `init_trace.js` depuis `https://www.v3ga.net/dessins_geometriques/init_trace.js` :
- Pour travailler hors-ligne ou versionner la librairie, téléchargez ce fichier et placez-le dans le dossier, puis modifiez la ligne `<script src="..."></script>` pour pointer sur `init_trace.js` local.

**Crédits & Licence**
- Librairie et travaux sources : v3ga — "Dessins géométriques et artistiques" (réadaptation p5.js). Voir https://github.com/v3ga/dessins_geometriques_et_artistiques
- La licence de la source originale est `GPL-2.0` (vérifier le dépôt d'origine pour détails). Respectez la licence si vous redistribuez ou hébergez ce projet.

**Améliorations possibles**
- Ajouter un champ pour personnaliser le nom du fichier exporté.
- Ajouter un indicateur de progression lors de la génération SVG pour grands dessins (N élevé).
- Intégrer `init_trace.js` en local et versionner la dépendance.

**Contact**
- Dépôt GitHub : https://github.com/Ilyas-efr/Etoile-BI
- Si vous souhaitez que je prépare un commit et pousse sur votre repo (ou que j'ajoute `init_trace.js` localement), dites-le et je m'en occupe.
