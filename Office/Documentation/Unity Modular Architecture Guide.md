
A concise guide for structuring Unity projects using **MVP + UseCases + Domain + VContainer** architecture with modular organization and proper lifetime management. Suitable for Obsidian notes.

---

## 1️⃣ High-Level Architecture
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

## 2️⃣ Project Folder Structure
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
    /Presentation

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
```

---

## 3️⃣ VContainer Code Examples

### App-Level: AppLifetimeScope
```csharp
using VContainer;
using VContainer.Unity;
using UnityEngine;

public class AppLifetimeScope : LifetimeScope
{
    [SerializeField] private AudioService audioServicePrefab;

    protected override void Configure(IContainerBuilder builder)
    {
        // Global Services
        builder.RegisterComponentInHierarchy(audioServicePrefab); // MonoBehaviour service
        builder.Register<SaveLoadService>(Lifetime.Singleton);   // Plain C# service
        builder.Register<UnityExceptionSource>(Lifetime.Singleton);
        builder.Register<AnalyticsService>(Lifetime.Singleton);

        // Global Domain
        builder.Register<PlayerWallet>(Lifetime.Singleton);
        builder.Register<Inventory>(Lifetime.Singleton);
    }
}
```

### Module-Level: ShopLifetimeScope
```csharp
using VContainer;
using VContainer.Unity;
using UnityEngine;

public class ShopLifetimeScope : LifetimeScope
{
    [SerializeField] private ShopView shopView;

    protected override void Configure(IContainerBuilder builder)
    {
        // Module Presentation
        builder.RegisterComponentInHierarchy(shopView);
        builder.Register<ShopPresenter>(Lifetime.Scoped);

        // Module UseCases
        builder.Register<BuyItemUseCase>(Lifetime.Scoped);
        builder.Register<RefreshShopUseCase>(Lifetime.Scoped);

        // Module Domain
        builder.Register<ShopItem>(Lifetime.Scoped);
        builder.Register<ShopRules>(Lifetime.Scoped);

        // Module Services
        builder.Register<ShopPricingService>(Lifetime.Scoped);
    }
}
```

- **AppLifetimeScope:** singleton/global objects that persist across the entire game
- **ModuleLifetimeScope:** scene or feature-specific objects, disposed when module/scene unloads
- Module scopes can access **App scope objects automatically**

---

## 4️⃣ Rules of Thumb: Global vs Module-local
| Decision | Global (App) | Module-local |
|----------|--------------|--------------|
| Used by multiple features? | ✅ | ❌ |
| Needs to persist across scenes? | ✅ | ❌ |
| Engine/platform dependency? | ✅ (service) | Usually no |
| Game rules tied to one feature? | ❌ | ✅ |
| Source of truth for entire game? | ✅ | ❌ |

---

## 5️⃣ Domain Guidelines
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

## 6️⃣ Services Guidelines
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

## 7️⃣ VContainer LifetimeScopes
| Scope | Lifetime | Typical use |
|-------|---------|-------------|
| AppLifetimeScope | Singleton | Global services & domain objects
| ModuleLifetimeScope | Scoped | Module presenters, use cases, feature domain
| Transient | Only for injection call | Stateless helpers

- Scene-bound ModuleLifetimeScope can access AppLifetimeScope objects
- Prevents singleton abuse, enables safe scene transitions

---

## 8️⃣ Naming Guidelines
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

## 9️⃣ Mental Model
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

## 10️⃣ Key Rules of Thumb
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

