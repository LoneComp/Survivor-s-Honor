# 🎮 Survivor's Honor

🇬🇧 English · [🇫🇷 Français](README.fr.md)

[![CI](https://github.com/LoneComp/Survivor-s-Honor/actions/workflows/ci.yml/badge.svg)](https://github.com/LoneComp/Survivor-s-Honor/actions/workflows/ci.yml)
![Unity](https://img.shields.io/badge/Unity-6000.2.9f1-black?logo=unity)
![Platform](https://img.shields.io/badge/platform-Windows-0078D6)

> Survival horror game with complex mechanics, large waves of zombies and procedural weapons. Beware of what you do, and where you do it. You will never know what you will encounter. Grab your resources, survive and explore.

---

## 🕹️ About

**Survivor's Honor** is a survival horror game built with **Unity 6**. Face waves of zombies, manage your resources, explore an unpredictable environment and deal with procedurally generated weapons.

## 🛠️ Tech stack

| | |
|---|---|
| **Engine** | Unity `6000.2.9f1` |
| **Target platform** | Windows (StandaloneWindows64) |
| **Large-file versioning** | Git LFS |
| **CI/CD** | GitHub Actions (GameCI) |

### Local development prerequisites
- **Unity Hub** + version **6000.2.9f1**
- **Git** and **Git LFS** (`git lfs install`)

```bash
git clone https://github.com/LoneComp/Survivor-s-Honor.git
cd Survivor-s-Honor
git lfs pull
```

---

## 🌿 Branches & naming convention

| Branch | Role |
|---|---|
| `main` | Stable production — **protected** (PR + review + CI required) |
| `Dev` | Integration — **protected** |
| *working branches* | Created from `Dev`/`main`, prefixed (see below) |

Every new branch **must** start with one of these prefixes (enforced by a *ruleset*):

| Prefix | Purpose | Example |
|---|---|---|
| `FT_` | New feature | `FT_inventory-drag-drop` |
| `FIX_` | Bug fix | `FIX_zombie-collision` |
| `HOTFIX_` | Urgent fix | `HOTFIX_menu-crash` |
| `DOC_` | Documentation | `DOC_readme-controls` |
| `REFACTO_` | Refactoring | `REFACTO_player-controller` |

> 💡 Branches created from an issue (`12-title`) must be renamed to `FT_12-title` to satisfy the convention.

---

## 🗂️ Kanban board

Work is tracked on the [**GitHub Projects board**](https://github.com/orgs/LoneComp/projects/1).

### Columns (`Status`)
| | Column | Meaning |
|---|---|---|
| 📋 | **Backlog** | Ideas / unplanned tasks |
| 🐛 | **Bug Backlog** | Bugs to fix |
| 🎯 | **Ready** | Ready to be picked up |
| 🚧 | **In Progress** | Being worked on |
| 👀 | **In Review** | PR open / under review |
| 🚫 | **Blocked** | Blocked (dependency, question) |
| ✅ | **Done** | Completed and merged |

### Fields
- **Priority** — 🔴 Urgent · 🟠 High · 🟡 Medium · 🟢 Low
- **Work Type** — ✨ Feature · 🐛 Bug · 🚑 Hotfix · 📝 Documentation · ♻️ Refactor

### Automations
- New issue → added to the board (**Backlog**)
- Issue closed / PR merged → **Done**
- Moving to **In Review**: manual when opening a PR

---

## 🔄 Contribution workflow

1. **Create an issue** on the [board](https://github.com/orgs/LoneComp/projects/1) (set `Priority` and `Work Type`).
2. From the issue, **Development** panel → **Create a branch**, then **prefix** the name (e.g. `FT_12-inventory`).
3. **Develop** and commit on that branch.
4. Open a **Pull Request** (to `Dev` or `main`) — fill in the template.
5. **CI** must be green (Tests + Build) and the review approved.
6. **Merge** → the linked issue closes automatically.

---

## 🤖 CI/CD

| Workflow | Trigger | Role |
|---|---|---|
| [`ci.yml`](.github/workflows/ci.yml) | PR, push to `main` | Tests (EditMode/PlayMode) + Windows build + Discord notifications |
| [`branch-naming.yml`](.github/workflows/branch-naming.yml) | PR | Validates the branch prefix |
| [`release.yml`](.github/workflows/release.yml) | tag `v*` | Build + GitHub Release publication |

### Publishing a release
```bash
git tag v0.1.0
git push origin v0.1.0
```
→ automatic build + GitHub Release with the zipped Windows executable.

### Tests
EditMode tests live in [`Assets/Tests/EditMode/`](Assets/Tests/EditMode/). Add your tests to that assembly; they run on every PR.

---

## 📦 Project structure

```
Assets/            # Code, scenes, prefabs, art
  Tests/EditMode/  # Unit tests
Packages/          # Unity dependencies (manifest.json)
ProjectSettings/   # Unity configuration
.github/workflows/ # CI/CD
```

---

*Made with ❤️ using Unity 6.*
