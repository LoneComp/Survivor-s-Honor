# Convention de Nommage Unity – README

Ce document définit les conventions de nommage pour organiser et développer votre projet Unity, avec des exemples concrets pour scripts, variables, classes et méthodes.

## Généralités
- Utilisez **PascalCase** pour les classes, méthodes et dossiers : chaque mot commence par une majuscule, pas d'espace ni de tiret.
- Utilisez **camelCase** pour les variables locales et paramètres : le premier mot en minuscule, suivants en majuscule.
- Préfixez les **champs privés** avec un underscore `_` en camelCase : `_currentHealth`.
- Utilisez **MAJUSCULES_AVEC_UNDERSCORE** pour les constantes : `MAX_SPEED`.
- Préfixez les **interfaces** par `I` majuscule : `IDamageable`.

---
## Exemples Concrets

### Classes, Scripts et Fichiers
```csharp
// Fichier : PlayerController.cs
public class PlayerController : MonoBehaviour {}

// Fichier : EnemyManager.cs
public class EnemyManager : MonoBehaviour {}
```

### Interfaces
```csharp
public interface IDamageable {
    void TakeDamage(float amount);
}
```

### Méthodes
```csharp
public void MovePlayer(Vector3 direction) {}
public bool IsGameOver() { return _isOver; }
public int GetScore() { return _score; }
```

### Variables locales et paramètres
```csharp
int playerScore;
float moveSpeed;
Vector3 startPosition;
```

### Champs privés
```csharp
private int _playerScore;
private float _moveSpeed;
private bool _isAlive;
```

### Propriétés publiques
```csharp
public int PlayerScore { get; private set; }
public bool IsAlive { get; private set; }
```

### Constantes
```csharp
private const float MAX_SPEED = 10.0f;
public const string GAME_VERSION = "1.0.0";
```

### Noms de dossiers
```
Scripts/
    Player/
        PlayerController.cs
    Enemies/
        EnemyManager.cs
        EnemyAI.cs
Materials/
    Characters/
    Environment/
```

### Namespace
```csharp
namespace MyCompany.MyProject.Gameplay.Player { ... }
```

---
## Bonnes pratiques
- Un seul MonoBehaviour par fichier.
- Les noms doivent refléter l’action ou le rôle (ex : `ApplyDamage`, `SaveManager`).
- Évitez les abréviations obscures. Préférez la clarté à la concision. 
- Les événements sont nommés avec une phrase verbale : `DoorOpened`, `PlayerDied`.
- Documentez toute exception à ces règles dans le projet.
