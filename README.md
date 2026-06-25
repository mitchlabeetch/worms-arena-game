# 🐛 Worms Arena — Clone de Worms Multijoueur

Un clone de Worms en pixel art, en français, avec multijoueur en ligne, terrain destructible, et personnalisation complète. Construit avec **React 18 + TypeScript + Vite + Tailwind CSS v4** et **Socket.io** pour le multijoueur.

![Build Status](https://img.shields.io/badge/build-passing-brightgreen)
![TypeScript](https://img.shields.io/badge/TypeScript-5.0-blue)
![React](https://img.shields.io/badge/React-18-61DAFB)
![Vite](https://img.shields.io/badge/Vite-5-646CFF)
![Electron](https://img.shields.io/badge/Electron-31-47848F)

## 🌐 Déploiement

- **Web (Cloudflare Pages)** : [https://worms-arena-web.pages.dev/](https://worms-arena-web.pages.dev/)
- **GitHub** : [https://github.com/mitchlabeetch/worms-arena-game](https://github.com/mitchlabeetch/worms-arena-game)

---

## ✨ Fonctionnalités

- 🎮 **Gameplay classique** : tour par tour, vers, armes, explosions, terrain destructible pixel par pixel
- 🌐 **Multijoueur en ligne** : salles, chat, hébergement de parties (Socket.io)
- 🎨 **Personnalisation complète** : nom du joueur, nom de l'équipe, couleur, skin des vers, noms individuels
- 🇫🇷 **Interface en français** avec messages drôles et réactions des vers
- 💥 **9 armes** : bazooka, grenade, fusil à pompe, dynamite, mine, frappe aérienne, boule de feu, téléportation, passer
- 🏝️ **6 thèmes de terrain** : île, désert, neige, forêt, volcan, caverne
- 🎵 **Système de particules** : fumée, débris, étincelles, éclaboussures d'eau, texte flottant
- 📷 **Caméra dynamique** : suivi, zoom, secousse lors des explosions
- 🌬️ **Vent affectant les projectiles**
- ⚰️ **Mort subite progressive** avec montée des eaux

---

## 🏗️ Architecture

```
worms-clone/
├── src/
│   ├── engine/           # Moteur de jeu (Canvas 2D)
│   │   ├── GameLoop.ts   # Boucle principale, tour de jeu, actions
│   │   ├── GameStore.ts  # État global (Zustand)
│   │   ├── Terrain.ts    # Terrain destructible procédural
│   │   ├── Camera.ts     # Caméra, zoom, shake
│   │   └── ParticleSystem.ts # Particules
│   ├── entities/         # Vers, projectiles, explosions
│   ├── weapons/          # Logique des armes
│   ├── ui/               # Écrans React
│   │   ├── screens/      # MainMenu, Lobby, HUD, Pause, GameOver
│   │   └── components/   # Boutons, panels
│   ├── multiplayer/      # Client multijoueur
│   │   └── SocketManager.ts
│   ├── i18n/             # Localisation FR
│   └── types.ts          # Types partagés
├── server/               # Serveur multijoueur (Express + Socket.io)
│   ├── src/
│   │   ├── index.ts      # Point d'entrée
│   │   ├── RoomManager.ts # Gestion des salles
│   │   └── types.ts      # Types serveur
│   └── package.json
├── plan.md               # Plan de développement
└── story_map.html        # User Story Map interactive
```

---

## 🚀 Démarrage rapide

### Client (Frontend)

```bash
# Installer les dépendances
npm install

# Lancer le serveur de développement
npm run dev

# Build de production
npm run build
```

### Serveur (Backend)

```bash
cd server

# Installer les dépendances
npm install

# Build TypeScript
npm run build

# Lancer le serveur
npm start

# Mode développement (watch)
npm run dev
```

Le serveur écoute sur le port **3001** par défaut.

---

## 🎯 Comment jouer

### En local (solo / hotseat)
1. Clique sur **Jouer** dans le menu principal
2. Personnalise ton équipe via **Personnaliser**
3. Utilise les flèches ou **Q/D** pour déplacer le ver
4. **Z/S** ou flèches haut/bas pour viser
5. **Espace** ou **Entrée** pour ouvrir le menu d'armes et tirer
6. **Échap** pour la pause, **Retour arrière** pour passer le tour

### En ligne (multijoueur)
1. Clique sur **Multijoueur**
2. Crée une salle ou rejoins-en une
3. Tous les joueurs doivent cliquer sur **Prêt**
4. L'hôte clique sur **Démarrer**

---

## 🎮 Contrôles

| Touche | Action |
|--------|--------|
| `←` / `Q` | Marcher à gauche |
| `→` / `D` | Marcher à droite |
| `↑` / `Z` | Augmenter l'angle |
| `↓` / `S` | Diminuer l'angle |
| `Espace` / `Entrée` | Ouvrir armes / Tirer |
| `Échap` | Pause |
| `Retour arrière` | Passer le tour |

---

## 🛠️ Technologies

- **Frontend** : React 18, TypeScript 5, Vite 5, Tailwind CSS 4
- **Backend** : Express, Socket.io, TypeScript
- **Rendu** : HTML5 Canvas 2D (pixel art)
- **État** : Zustand
- **Desktop** : Electron + electron-builder
- **Style** : Tailwind CSS avec thème pixel

---

## 💻 Build Desktop (Electron)

Le jeu est empaqueté avec **Electron** pour Windows, Linux et macOS.

```bash
cd electron
npm install

# Windows (NSIS installer + portable)
npm run build:win

# Linux (tar.gz)
npm run build:linux

# macOS (zip) — nécessite macOS
npm run build:mac
```

### ⚠️ Note pour le CI/CD

Le workflow GitHub Actions pour les builds automatiques est disponible à `github/workflows/build-desktop.yml`. Il doit être déplacé manuellement vers `.github/workflows/build-desktop.yml` pour que GitHub Actions le détecte. Pour ce faire :

1. Allez sur https://github.com/mitchlabeetch/worms-arena-game
2. Cliquez sur **Actions** → **New workflow** → **set up a workflow yourself**
3. Collez le contenu du fichier `github/workflows/build-desktop.yml`
4. Nommez le fichier `.github/workflows/build-desktop.yml`
5. Committez

---

## 📝 License

MIT — Fait avec ❤️ et beaucoup de cafés.

Inspiré par **Worms Armageddon**.