
A concise guide for structuring Unity projects using **MVP + UseCases + Domain + VContainer** architecture with modular organization and proper lifetime management. Suitable for Obsidian notes.

---

## 1. High-Level Architecture
```
User Input
     ↓
View (MonoBehaviour)  → displays data, forwards input
     ↓
Presenter (UI state + orchestration)
     ↓
UseCase (Business logic / module logic)
     ↓
Domain (Data + rules / canonical state)
     ↓
(Service optional for side effects, Unity/platform interaction)
```

- **View:** Dumb UI, only renders and forwards events
- **Presenter:** Manages UI state, subscribes to Domain/Service events, orchestrates UseCases
- **UseCase:** Orchestrates meaningful actions, calls Domain, may use Services
- **Domain:** Pure C# models with data and rules, source of truth
- **Service:** Provides engine/platform or external functionality, side-effects only
- **VContainer:** Handles dependency injection and lifetime scopes

---

## 2. Project Folder Structure
```
/Assets/Scripts
  /App
    /Composition
      AppLifetimeScope.cs
    /Infrastructure
      AudioService.cs (MonoBehaviour prefab if needed)
      SaveLoadService.cs
      UnityExceptionSource.cs (MonoBehaviour prefab)
      AnalyticsService.cs
    /Domain
      PlayerWallet.cs
      Inventory.cs

  /Modules
    /Shop
      /Composition
        ShopLifetimeScope.cs
      /Domain
        ShopItem.cs
        ShopRules.cs
      /UseCases
        BuyItemUseCase.cs
        RefreshShopUseCase.cs
      /Services
        ShopPricingService.cs
      /Presentation
        /Views
          ShopView.cs
        /Presenters
          ShopPresenter.cs

    /Match
      /Composition
        MatchLifetimeScope.cs
      /Domain
        Match.cs
        Hole.cs
      /UseCases
        TakeShotUseCase.cs
        EndHoleUseCase.cs
      /Services
        MatchTimerService.cs
      /Presentation
        /Views
          ScoreView.cs
        /Presenters
          ScorePresenter.cs
```

### Layer Roles
- **App/Composition:** Global DI wiring, global LifetimeScope
- **App/Infrastructure:** Cross-cutting services or engine/platform adapters
- **App/Domain:** Global game state (shared across modules)
- **Module/Composition:** Module-specific DI wiring
- **Module/Domain:** Module-local state & rules
- **Module/UseCases:** Module actions or orchestration
- **Module/Services:** Feature-specific helpers or adapters
- **Module/Presentation:** Views (MonoBehaviour) + Presenters

---

## 3. Rules of Thumb: Global vs Module-local
| Decision | Global (App) | Module-local |
|----------|--------------|--------------|
| Used by multiple features? | ✅ | ❌ |
| Needs to persist across scenes? | ✅ | ❌ |
| Engine/platform dependency? | ✅ (service) | Usually no |
| Game rules tied to one feature? | ❌ | ✅ |
| Source of truth for entire game? | ✅ | ❌ |

---

## 4. Domain Guidelines
- **Combine data + rules in one class** unless rules span multiple models
- Example:
```csharp
public class PlayerWallet {
    public int Coins { get; private set; }
    public bool CanAfford(int amount) => Coins >= amount;
    public void Spend(int amount) {
        if (!CanAfford(amount)) throw new InvalidOperationException();
        Coins -= amount;
    }
}
```
- **Domain Services** (separate) only for rules spanning multiple entities
- Keep **Domain pure C#**: no Unity, no MonoBehaviour, no UI

---

## 5. Services Guidelines
- **App-level services:** Cross-cutting, reusable across modules
  - AudioService, SaveLoadService, AnalyticsService, UnityExceptionSource
- **Module-level services:** Feature-specific helpers
  - ShopPricingService, MatchTimerService
- **MonoBehaviour?** Only if service needs Unity lifecycle, GameObject, Coroutine, or AudioSource
- **Prefab?** Use prefab + DontDestroyOnLoad for global MonoBehaviour services
- **Do not update Views directly**: emit events, Presenter subscribes

Example `UnityExceptionSource`:
```csharp
public class UnityExceptionSource : MonoBehaviour {
    public event Action<string> ExceptionRaised;
    private void OnEnable() => Application.logMessageReceived += HandleLog;
    private void OnDisable() => Application.logMessageReceived -= HandleLog;
    private void HandleLog(string condition, string stackTrace, LogType type) {
        if (type == LogType.Exception) ExceptionRaised?.Invoke(condition);
    }
}
```

---

## 6. VContainer LifetimeScopes
| Scope | Lifetime | Typical use |
|-------|---------|-------------|
| AppLifetimeScope | Singleton | Global services & domain objects
| ModuleLifetimeScope | Scoped | Module presenters, use cases, feature domain
| Transient | Only for injection call | Stateless helpers

- Scene-bound ModuleLifetimeScope can access AppLifetimeScope objects
- Prevents singleton abuse, enables safe scene transitions

---

## 7. Naming Guidelines
| Layer | Naming |
|-------|--------|
| Domain | `Noun` (PlayerWallet, Hole) |
| UseCase | `Verb + UseCase` (BuyItemUseCase) |
| Presenter | `Feature + Presenter` (ShopPresenter) |
| View | `Feature + View` (ShopView) |
| Service | `Thing + Service` (AudioService) |
| Adapter/External | `UnityXxxSource` / `XxxGateway` |
| LifetimeScope | `FeatureLifetimeScope` |

---

## 8. Mental Model
```
AppLifetimeScope (global)
   ├─ Global services (AudioService, SaveLoadService)
   └─ Global domain (PlayerWallet, Inventory)

ModuleLifetimeScope (scene/module)
   ├─ Module presenters
   ├─ Module use cases
   ├─ Module domain (feature-specific)
   └─ Module services (feature-specific)

Data Flow Example:
User clicks → View → Presenter → UseCase → Domain → Service (side effects) → Presenter → View
```

---

## 9. Key Rules of Thumb
1. Keep Domain pure and cohesive (data + rules in one class unless spanning multiple entities)
2. Module self-contained: domain, use cases, presenters, views, feature services
3. Global shared things: App/Domain, App/Infrastructure, AppLifetimeScope
4. MonoBehaviour Service only if it needs Unity lifecycle
5. Composition folders are only for dependency wiring (VContainer LifetimeScopes)
6. Never let Services update Views directly; use events and Presenters
7. Prefabs for global MonoBehaviour services for persistence across scenes

---
**This structure ensures:**
- Modular, maintainable code
- Testable domain and use cases
- Clear dependency direction
- Safe scene transitions and global state management

--------------------------------------------------------

- **Clean Code** — polish your coding fundamentals
    
- **Design Patterns (GoF)** — learn reusable design structures
    
- **Clean Architecture** — understand layers and dependencies
    
- **Working with Legacy Code** — refactor safely
    
- **Implementing DDD** — bring domain modeling into practice
    
- **Domain‑Driven Design (Evans)** — deep dive into domain modeling
    
- **Game Programming Patterns** — game‑specific structural wisdom

