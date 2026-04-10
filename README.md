# 📄 PDFMaster

**Votre iLovePDF personnel — 100% gratuit, 100% local, zéro limite.**

> Convertir · Fusionner · Compresser · Pivoter · OCR  
> Aucun fichier n'est envoyé sur internet. Tout se passe dans votre navigateur.

---

## ✨ Fonctionnalités

| Outil | Description |
|-------|-------------|
| 🖼 **Images → PDF** | Convertit JPG, PNG, WEBP, GIF en PDF · format A4/Letter/Original · marges · qualité |
| 📄 **PDF → Images** | Extrait chaque page en JPG ou PNG · 72/150/300 dpi |
| 🔗 **Fusionner** | Combine plusieurs PDFs en un seul · nombre illimité |
| 📦 **Compresser** | Réduit le poids d'une image · gain affiché en % |
| 🔄 **Pivoter** | Rotation 90°/180°/270° · miroir horizontal et vertical |
| 🔍 **OCR** | Extrait le texte d'une image ou d'un scan · FR/EN/ES/DE |

---

## 🎨 4 Thèmes inclus

- 🌙 **Nuit** — futuriste violet sombre
- ☀️ **Soleil** — chaud et lumineux
- 🌿 **Forêt** — vert organique
- 🌊 **Océan** — bleu tech professionnel

---

## 🚀 Installation en local (PC / Mac / Linux)

### Option 1 — La plus simple : ouvrir directement

```bash
# 1. Télécharger le projet
git clone https://github.com/TON-USERNAME/pdfmaster.git

# 2. Aller dans le dossier
cd pdfmaster

# 3. Ouvrir dans le navigateur
# Sur Mac :
open index.html

# Sur Windows (double-clic ou) :
start index.html

# Sur Linux :
xdg-open index.html
```

> ⚠️ **Note** : Pour que la PWA (installation sur bureau) fonctionne,
> il faut servir les fichiers via un serveur local (voir Option 2).

---

### Option 2 — Avec VS Code + Live Server (recommandé)

1. **Installer [VS Code](https://code.visualstudio.com/)**
2. **Installer l'extension Live Server** (par Ritwick Dey)
   - `Ctrl+Shift+X` → chercher "Live Server" → Installer
3. **Ouvrir le dossier** dans VS Code :
   - `Fichier` → `Ouvrir le dossier` → sélectionner `pdfmaster/`
4. **Clic droit** sur `index.html` → **"Open with Live Server"**
5. L'app s'ouvre sur `http://127.0.0.1:5500` 🎉

---

### Option 3 — Avec Python (si installé)

```bash
cd pdfmaster
python -m http.server 8080
# Ouvrir http://localhost:8080
```

---

### Option 4 — Avec Node.js

```bash
cd pdfmaster
npx serve .
# Ouvrir l'URL affichée dans le terminal
```

---

## 📲 Installer l'app sur votre bureau (PWA)

Une fois l'app ouverte via un serveur local ou en ligne :

### Sur Chrome / Edge (PC & Mac)
1. Ouvrir l'app dans le navigateur
2. Cliquer sur le bouton **"⬇ Installer l'app"** dans le header
   — OU —
   Cliquer sur l'icône ⊕ dans la barre d'adresse
3. Confirmer → l'app apparaît sur votre bureau comme un vrai logiciel !

### Sur iPhone / iPad (Safari)
1. Ouvrir l'URL dans Safari
2. Appuyer sur **Partager** (icône carré avec flèche)
3. **"Sur l'écran d'accueil"**
4. Confirmer → l'icône apparaît sur votre écran d'accueil

### Sur Android (Chrome)
1. Ouvrir l'URL dans Chrome
2. Menu ⋮ → **"Ajouter à l'écran d'accueil"**
3. Confirmer

---

## 🌐 Héberger gratuitement en ligne (Netlify)

```
1. Créer un compte sur https://netlify.com (gratuit)
2. Aller sur https://app.netlify.com
3. Glisser-déposer le dossier pdfmaster/ dans la zone de dépôt
4. ✅ Votre app est en ligne ! URL du type : https://pdfmaster-xxx.netlify.app
```

---

## 🔌 Extension Chrome

Pour utiliser PDFMaster comme extension dans votre navigateur :

1. Copier `index.html` → renommer en `popup.html`
2. Ajouter dans le `<head>` : `<style>body{width:800px;min-height:500px}</style>`
3. Créer `manifest.json` dans le dossier :

```json
{
  "manifest_version": 3,
  "name": "PDFMaster",
  "version": "1.0",
  "description": "Outils PDF locaux gratuits",
  "action": {
    "default_popup": "popup.html",
    "default_icon": { "128": "icon512.png" }
  }
}
```

4. Dans Chrome : `chrome://extensions` → **Mode développeur** → **Charger l'extension**
5. Sélectionner le dossier → l'icône apparaît dans Chrome !

---

## 🖥️ Application Desktop (Electron)

Pour créer un vrai logiciel installable (.exe / .dmg / .AppImage) :

```bash
# Prérequis : Node.js (https://nodejs.org)

cd pdfmaster
npm init -y
npm install electron electron-builder --save-dev

# Créer main.js avec ce contenu :
```

```javascript
const { app, BrowserWindow } = require('electron')
const path = require('path')

function createWindow() {
  const win = new BrowserWindow({ width: 1100, height: 750, title: 'PDFMaster' })
  win.loadFile('index.html')
}

app.whenReady().then(createWindow)
app.on('window-all-closed', () => { if (process.platform !== 'darwin') app.quit() })
```

```bash
# Tester
npx electron .

# Compiler (Windows)
npx electron-builder --win    # → génère un .exe dans /dist

# Compiler (Mac)
npx electron-builder --mac    # → génère un .dmg dans /dist
```

---

## 📁 Structure du projet

```
pdfmaster/
├── index.html      ← Application principale (tout-en-un)
├── manifest.json   ← Configuration PWA
├── sw.js           ← Service Worker (cache hors-ligne)
├── icon192.png     ← Icône PWA 192×192
├── icon512.png     ← Icône PWA 512×512
└── README.md       ← Ce fichier
```

---

## 🛠️ Technologies utilisées

- **[jsPDF](https://github.com/parallax/jsPDF)** — création de PDFs
- **[pdf-lib](https://pdf-lib.js.org/)** — fusion et manipulation de PDFs
- **[PDF.js](https://mozilla.github.io/pdf.js/)** — lecture/rasterisation de PDFs (Mozilla)
- **[Tesseract.js](https://tesseract.projectnaptha.com/)** — OCR (reconnaissance de texte)
- **Canvas API** — compression et transformation d'images
- **PWA** — installation sur bureau/mobile

> Tout fonctionne **dans le navigateur**, aucun serveur requis.

---

## 🤝 Contribuer

Les contributions sont les bienvenues !

```bash
git fork https://github.com/TON-USERNAME/pdfmaster
git checkout -b feature/ma-fonctionnalite
git commit -m "Ajout : ma fonctionnalité"
git push origin feature/ma-fonctionnalite
# → Ouvrir une Pull Request
```

---

## 📄 Licence

MIT — libre d'utilisation, de modification et de distribution.

---

*Fait avec ❤️ · Inspiré par iLovePDF · Entièrement local · Entièrement gratuit*
