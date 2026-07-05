# 🎮 Survivor's Honor

[![CI](https://github.com/LoneComp/Survivor-s-Honor/actions/workflows/ci.yml/badge.svg)](https://github.com/LoneComp/Survivor-s-Honor/actions/workflows/ci.yml)
![Unity](https://img.shields.io/badge/Unity-6000.2.9f1-black?logo=unity)
![Platform](https://img.shields.io/badge/platform-Windows-0078D6)

> Survival horror game with complex mechanics, large waves of zombies and procedural weapons. Beware of what you do, and where you do it. You will never know what you will encounter. Grab your resources, survive and explore.

---

## 🕹️ À propos

**Survivor's Honor** est un jeu de survival horror développé sous **Unity 6**. Affronte des vagues de zombies, gère tes ressources, explore un environnement imprévisible et compose avec des armes procédurales.

## 🛠️ Stack technique

| | |
|---|---|
| **Moteur** | Unity `6000.2.9f1` |
| **Plateforme cible** | Windows (StandaloneWindows64) |
| **Versioning gros fichiers** | Git LFS |
| **CI/CD** | GitHub Actions (GameCI) |

### Prérequis pour développer en local
- **Unity Hub** + version **6000.2.9f1**
- **Git** et **Git LFS** (`git lfs install`)

```bash
git clone https://github.com/LoneComp/Survivor-s-Honor.git
cd Survivor-s-Honor
git lfs pull
```

---

## 🌿 Branches & convention de nommage

| Branche | Rôle |
|---|---|
| `main` | Production stable — **protégée** (PR + review + CI obligatoires) |
| `Dev` | Intégration — **protégée** |
| *branches de travail* | Créées depuis `Dev`/`main`, préfixées (voir ci-dessous) |

Toute nouvelle branche **doit** commencer par un de ces préfixes (imposé par un *ruleset*) :

| Préfixe | Usage | Exemple |
|---|---|---|
| `FT_` | Nouvelle fonctionnalité | `FT_inventaire-drag-drop` |
| `FIX_` | Correction de bug | `FIX_collision-zombie` |
| `HOTFIX_` | Correctif urgent | `HOTFIX_crash-menu` |
| `DOC_` | Documentation | `DOC_readme-controls` |
| `REFACTO_` | Refactoring | `REFACTO_player-controller` |

> 💡 Les branches créées depuis une issue (`12-titre`) doivent être renommées en `FT_12-titre` pour respecter la convention.

---

## 🗂️ Tableau Kanban

Le suivi se fait sur le [**board GitHub Projects**](https://github.com/orgs/LoneComp/projects/1).

### Colonnes (`Status`)
| | Colonne | Signification |
|---|---|---|
| 📋 | **Backlog** | Idées / tâches non planifiées |
| 🐛 | **Bug Backlog** | Bugs à traiter |
| 🎯 | **Ready** | Prêt à être pris |
| 🚧 | **In Progress** | En cours de développement |
| 👀 | **In Review** | PR ouverte / en relecture |
| 🚫 | **Blocked** | Bloqué (dépendance, question) |
| ✅ | **Done** | Terminé et mergé |

### Champs
- **Priority** — 🔴 Urgent · 🟠 High · 🟡 Medium · 🟢 Low
- **Work Type** — ✨ Feature · 🐛 Bug · 🚑 Hotfix · 📝 Documentation · ♻️ Refactor

### Automatisations
- Nouvelle issue → ajoutée au board (**Backlog**)
- Issue fermée / PR mergée → **Done**
- Passage en **In Review** : manuel à l'ouverture de la PR

---

## 🔄 Workflow de contribution

1. **Créer une issue** sur le [board](https://github.com/orgs/LoneComp/projects/1) (renseigne `Priority` et `Work Type`).
2. Depuis l'issue, panneau **Development** → **Create a branch**, puis **préfixe** le nom (ex. `FT_12-inventaire`).
3. **Développe** et commit sur cette branche.
4. Ouvre une **Pull Request** (vers `Dev` ou `main`) — remplis le template.
5. La **CI** doit être verte (Tests + Build) et la review approuvée.
6. **Merge** → l'issue liée se ferme automatiquement.

---

## 🤖 CI/CD

| Workflow | Déclencheur | Rôle |
|---|---|---|
| [`ci.yml`](.github/workflows/ci.yml) | PR, push sur `main` | Tests (EditMode/PlayMode) + Build Windows + notifs Discord |
| [`branch-naming.yml`](.github/workflows/branch-naming.yml) | PR | Vérifie le préfixe de la branche |
| [`release.yml`](.github/workflows/release.yml) | tag `v*` | Build + publication d'une Release GitHub |

### Publier une release
```bash
git tag v0.1.0
git push origin v0.1.0
```
→ build automatique + Release GitHub avec l'exécutable Windows zippé.

### Tests
Les tests EditMode vivent dans [`Assets/Tests/EditMode/`](Assets/Tests/EditMode/). Ajoute tes tests dans cette assembly ; ils tournent à chaque PR.

---

## 📦 Structure du projet

```
Assets/            # Code, scènes, prefabs, art
  Tests/EditMode/  # Tests unitaires
Packages/          # Dépendances Unity (manifest.json)
ProjectSettings/   # Configuration Unity
.github/workflows/ # CI/CD
```

---

*Développé avec ❤️ sous Unity 6.*
