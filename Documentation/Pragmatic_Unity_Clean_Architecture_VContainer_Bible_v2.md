# Pragmatic Clean Architecture for Unity + VContainer
## A Long-Term Reference Guide

> **Goal:** Keep a Unity project easy to change, test, and understand **without fighting Unity or creating unnecessary architectural ceremony**.

This guide is a pragmatic synthesis of Clean Architecture, feature-based organization, MVP/presentation separation, Dependency Injection, and VContainer.

---

# 0. The Architecture in One Picture

```text
                         ┌─────────────────────────────┐
                         │         UNITY WORLD         │
                         │ Scenes / Prefabs / UI / MBs │
                         └──────────────┬──────────────┘
                                        │
                                  player input /
                                   Unity events
                                        │
                                        ▼
                         ┌─────────────────────────────┐
                         │        PRESENTATION         │
                         │ Views / Controllers /       │
                         │ Presenters                  │
                         └──────────────┬──────────────┘
                                        │
                                        ▼
                         ┌─────────────────────────────┐
                         │        APPLICATION          │
                         │ Feature Services /          │
                         │ Important Use Cases         │
                         └──────────────┬──────────────┘
                                        │
                                        ▼
                         ┌─────────────────────────────┐
                         │           DOMAIN            │
                         │ Rules / State / Concepts    │
                         │ Pure C# where practical     │
                         └──────────────┬──────────────┘
                                        │
                            ports/interfaces when needed
                                        │
              ┌─────────────────────────┴──────────────────────────┐
              ▼                                                    ▼
     ┌──────────────────────┐                           ┌──────────────────────┐
     │    INFRASTRUCTURE    │                           │ UNITY IMPLEMENTATION │
     │ Save / Backend / SDK │                           │ Rigidbody / Animator │
     │ Analytics / IAP etc. │                           │ Audio / Rendering    │
     └──────────────────────┘                           └──────────────────────┘

                Everything is assembled by VContainer LifetimeScopes.
```

The important rule is **dependency direction**, not folder purity:

```text
Presentation ──► Application ──► Domain

Infrastructure ──implements──► interfaces required by inner code

Composition Root knows everyone.
Everyone else should know only what they need.
```

---

# 1. The Five Questions to Ask When Creating a Class

When unsure where something belongs, ask these in order.

## 1. Is this a game rule or meaningful game state?

Examples:

- wallet balance
- owned inventory
- equipment upgrade rules
- tournament scoring
- mission completion rules
- XP requirements
- purchase eligibility
- shot calculation rules

**Yes → Domain**

---

## 2. Is this coordinating a meaningful operation?

Examples:

- purchase an item
- claim a reward
- equip an outfit
- complete a match
- submit a tournament result
- load player profile

**Yes → Application**

---

## 3. Is this displaying something or reacting to player/UI input?

Examples:

- screen
- popup
- button handler
- HUD
- list item
- UI animation
- Presenter

**Yes → Presentation**

---

## 4. Is this talking to technology outside your game rules?

Examples:

- JSON
- PlayerPrefs
- filesystem
- Nakama
- Firebase
- Adjust
- Unity IAP
- ads
- REST APIs
- platform services

**Yes → Infrastructure**

---

## 5. Is this simply using Unity to make the game exist in the scene?

Examples:

- Rigidbody
- Collider
- Animator
- Camera
- particle system
- GameObject pooling component
- NavMeshAgent
- scene loading component

This is **Unity-facing implementation code**.

It may live inside the feature that owns it. It does **not automatically belong in Infrastructure**.

---

# 2. Domain vs Application — The Confusing Part

This distinction becomes much easier if you stop thinking:

```text
Domain = important code
Application = less important code
```

Instead use:

```text
DOMAIN      = knows the rules.
APPLICATION = knows the workflow.
```

---

## Domain Example

```csharp
public sealed class Wallet
{
    public int Coins { get; private set; }

    public Wallet(int coins)
    {
        Coins = coins;
    }

    public bool CanAfford(int amount)
        => amount >= 0 && Coins >= amount;

    public void Spend(int amount)
    {
        if (!CanAfford(amount))
            throw new InvalidOperationException("Insufficient coins.");

        Coins -= amount;
    }

    public void Add(int amount)
    {
        if (amount < 0)
            throw new ArgumentOutOfRangeException(nameof(amount));

        Coins += amount;
    }
}
```

`Wallet` knows:

> You cannot spend more coins than you own.

It does **not** know:

- which button was clicked
- where data is saved
- what analytics event is sent
- which backend exists
- which screen refreshes

That is Domain.

---

## Application Example

```csharp
public sealed class ShopService
{
    private readonly IPlayerRepository _players;
    private readonly IShopCatalog _catalog;

    public ShopService(
        IPlayerRepository players,
        IShopCatalog catalog)
    {
        _players = players;
        _catalog = catalog;
    }

    public PurchaseResult Buy(ItemId itemId)
    {
        var player = _players.Current;
        var item = _catalog.Get(itemId);

        if (!player.Wallet.CanAfford(item.Price))
            return PurchaseResult.InsufficientFunds;

        player.Wallet.Spend(item.Price);
        player.Inventory.Add(item.Id);

        _players.Save();

        return PurchaseResult.Success;
    }
}
```

`ShopService` knows the sequence:

```text
Find item
   ↓
Check wallet
   ↓
Spend
   ↓
Grant item
   ↓
Save
```

That is Application.

The **rule** `Wallet.CanAfford()` belongs to Domain.

The **workflow** that combines wallet + inventory + repository belongs to Application.

---

# 3. Don't Force a Domain Layer Where There Is No Domain

This is extremely important.

Suppose you make a simple credits popup:

```text
CreditsPopup
CloseButton
ScrollRect
```

You do not need:

```text
CreditsDomain
CreditsApplicationService
CreditsPresenter
CreditsRepository
```

Just make:

```text
Credits/
└── CreditsView.cs
```

Architecture should scale **with complexity**.

---

# 4. Recommended Feature-Based Project Structure

Prefer vertical modules.

```text
Assets/
└── Game/
    ├── Bootstrap/
    │   ├── ProjectLifetimeScope.cs
    │   └── SceneLoader.cs
    │
    ├── Features/
    │   ├── Inventory/
    │   │   ├── Domain/
    │   │   ├── Application/
    │   │   ├── Presentation/
    │   │   ├── Infrastructure/
    │   │   └── Composition/
    │   │
    │   ├── Shop/
    │   │   ├── Domain/
    │   │   ├── Application/
    │   │   ├── Presentation/
    │   │   └── Composition/
    │   │
    │   ├── Wardrobe/
    │   │   ├── Domain/
    │   │   ├── Application/
    │   │   ├── Presentation/
    │   │   └── Composition/
    │   │
    │   └── Gameplay/
    │       ├── Domain/
    │       ├── Application/
    │       ├── Presentation/
    │       └── Composition/
    │
    ├── Shared/
    │   ├── Save/
    │   ├── Analytics/
    │   ├── Networking/
    │   ├── Audio/
    │   ├── Time/
    │   └── Common/
    │
    └── Config/
        └── ScriptableObjects/
```

Do **not** create empty folders just to satisfy architecture.

A feature can legitimately be:

```text
SmallPopup/
└── Presentation/
```

or:

```text
Economy/
├── Domain/
├── Application/
└── Infrastructure/
```

---

# 5. MonoBehaviours: Where Do They Belong?

## Rule

> `MonoBehaviour` tells you **what framework a class uses**, not **what architectural responsibility it has**.

Therefore:

```text
MonoBehaviour != Infrastructure
```

Classify by responsibility.

---

## Presentation MonoBehaviours

```csharp
public sealed class ShopView : MonoBehaviour
{
    [SerializeField] Button buyButton;
    [SerializeField] TMP_Text balanceText;

    public event Action BuyPressed;

    private void Awake()
    {
        buyButton.onClick.AddListener(
            () => BuyPressed?.Invoke());
    }

    public void SetBalance(int value)
    {
        balanceText.text = value.ToString();
    }
}
```

This belongs in:

```text
Shop/Presentation/
```

---

## Gameplay/Unity MonoBehaviours

```csharp
public sealed class BallBody : MonoBehaviour
{
    [SerializeField] Rigidbody body;

    public void Launch(Vector3 velocity)
    {
        body.linearVelocity = velocity;
    }
}
```

This belongs with the gameplay feature.

For example:

```text
Gameplay/Presentation/
```

or, if your team prefers a clearer name:

```text
Gameplay/Unity/
```

You do **not** need to force it into Infrastructure.

---

## Infrastructure MonoBehaviours

Some MonoBehaviours genuinely are infrastructure:

```csharp
public sealed class AdjustAnalyticsAdapter : MonoBehaviour, IAnalytics
{
    public void Track(string eventName)
    {
        // Adjust SDK call
    }
}
```

or:

```csharp
public sealed class UnityIapAdapter : MonoBehaviour, IPaymentGateway
{
}
```

These belong in Infrastructure because their **responsibility** is external technology.

---

# 6. Persistent Runtime Data: Do NOT Default to MonoBehaviour Singletons

Avoid making your game state:

```csharp
public class PlayerData : MonoBehaviour
{
    public static PlayerData Instance;
}
```

and then calling:

```csharp
PlayerData.Instance.Coins
```

from everywhere.

This creates:

- hidden dependencies
- difficult tests
- order-of-initialization problems
- scene lifetime problems
- global mutable state
- tight coupling

With VContainer, there is usually a better solution.

---

# 7. Recommended Runtime State Model

Use a plain C# session object.

```csharp
public sealed class PlayerSession
{
    public PlayerProfile Profile { get; private set; }

    public bool IsLoaded => Profile != null;

    public void SetProfile(PlayerProfile profile)
    {
        Profile = profile;
    }

    public void Clear()
    {
        Profile = null;
    }
}
```

Register it at the lifetime that actually matches the data.

```csharp
builder.Register<PlayerSession>(Lifetime.Singleton);
```

**Important:** In VContainer, `Singleton` means singleton **within that container hierarchy/lifetime setup**, not "make a global static."

Your code receives it through DI:

```csharp
public sealed class InventoryService
{
    private readonly PlayerSession _session;

    public InventoryService(PlayerSession session)
    {
        _session = session;
    }
}
```

No:

```text
PlayerSession.Instance
```

required.

---

# 8. Runtime State vs Persistent Storage

Do not confuse:

```text
PlayerSession
```

with:

```text
PlayerRepository
```

They have different jobs.

```text
                    runtime memory
                         │
                         ▼
                  PlayerSession
                         │
                         │ save/load
                         ▼
                IPlayerRepository
                         │
                         ▼
            Nakama / JSON / Cloud Save
```

---

## Runtime Session

```csharp
public sealed class PlayerSession
{
    public PlayerProfile Profile { get; private set; }
}
```

Fast in-memory state used during the game.

---

## Repository

```csharp
public interface IPlayerRepository
{
    Task<PlayerProfile> LoadAsync();
    Task SaveAsync(PlayerProfile profile);
}
```

Repository answers:

> Where does persistent player data come from / go to?

Implementation:

```csharp
public sealed class NakamaPlayerRepository : IPlayerRepository
{
    public Task<PlayerProfile> LoadAsync()
    {
        // Nakama implementation
    }

    public Task SaveAsync(PlayerProfile profile)
    {
        // Nakama implementation
    }
}
```

---

# 9. Should Other Modules Access Data Through Repositories?

Usually **no**.

Bad:

```text
ShopPresenter
     ↓
IPlayerRepository
```

Presentation shouldn't normally dig directly into persistence.

Prefer:

```text
ShopView
   ↓
ShopPresenter
   ↓
ShopService
   ↓
PlayerSession / Domain
   ↓
IPlayerRepository when persistence is required
```

A repository is a persistence boundary, not your universal state-access API.

---

# 10. Don't Make a Repository Around Every Object

Repository is appropriate when something represents meaningful persisted data.

Good candidates:

```text
IPlayerRepository
IInventoryRepository
IProgressRepository
IRemoteConfigRepository
ITournamentRepository
```

Usually poor candidates:

```text
ICameraRepository
IButtonRepository
IPopupRepository
IGolfBallRepository
```

unless the problem genuinely involves persistence/querying.

---

# 11. VContainer: The Recommended Lifetime Hierarchy

For most games, use three conceptual levels.

```text
PROJECT / APP SCOPE
ProjectLifetimeScope
        │
        ├── Save
        ├── Backend
        ├── Analytics
        ├── Authentication
        ├── PlayerSession
        ├── Audio
        └── SceneLoader
        │
        ▼
SCENE / GAME MODE SCOPE
GameSceneLifetimeScope
        │
        ├── MatchService
        ├── Gameplay presenters
        ├── Scene views
        └── Scene-specific state
        │
        ▼
OPTIONAL FEATURE / TEMPORARY SCOPE
TournamentLifetimeScope
PopupFlowLifetimeScope
MatchLifetimeScope
etc.
```

VContainer supports parent/child `LifetimeScope`s, including dynamically created child scopes and additive scene parenting. That makes this hierarchy a natural fit.

---

# 12. Master Composition Root

Yes, keep one application-level root.

Example:

```csharp
public sealed class ProjectLifetimeScope : LifetimeScope
{
    protected override void Configure(IContainerBuilder builder)
    {
        builder.Register<PlayerSession>(Lifetime.Singleton);

        builder.Register<IPlayerRepository, NakamaPlayerRepository>(
            Lifetime.Singleton);

        builder.Register<IAnalytics, AdjustAnalyticsAdapter>(
            Lifetime.Singleton);

        builder.Register<ISaveService, SaveService>(
            Lifetime.Singleton);

        builder.Register<SceneLoader>(Lifetime.Singleton);
    }
}
```

This scope should contain things that genuinely survive across much of the application.

Think:

```text
"Would this still conceptually exist if I change scenes?"
```

If yes, it may belong here.

---

# 13. Should Every Module Have a Composition Root?

## Short answer

**Give a module registration/composition file when the module has enough dependencies to justify it.**

Do not automatically create one `LifetimeScope` GameObject per tiny module.

There are two good approaches.

---

## Approach A — Scene LifetimeScope + Module Installers

Recommended default.

```csharp
public sealed class MainMenuLifetimeScope : LifetimeScope
{
    protected override void Configure(IContainerBuilder builder)
    {
        InventoryComposition.Register(builder);
        ShopComposition.Register(builder);
        WardrobeComposition.Register(builder);

        builder.RegisterComponentInHierarchy<MainMenuView>();
    }
}
```

Module:

```csharp
public static class ShopComposition
{
    public static void Register(IContainerBuilder builder)
    {
        builder.Register<ShopService>(Lifetime.Scoped);
        builder.RegisterEntryPoint<ShopPresenter>();
    }
}
```

Result:

```text
MainMenuLifetimeScope
      │
      ├── ShopComposition
      ├── WardrobeComposition
      └── InventoryComposition
```

This gives modules ownership of their registrations without creating many unnecessary nested scopes.

**This is my recommended default.**

---

# 14. When a Module Deserves Its Own Child LifetimeScope

Use an actual child `LifetimeScope` when the feature has a meaningful independent lifetime.

Examples:

```text
Match starts → create MatchLifetimeScope
Match ends   → dispose MatchLifetimeScope
```

or:

```text
Large feature scene loads → scope created
Feature scene unloads     → scope disposed
```

or:

```text
Temporary gameplay mode
Tournament session
Large modal flow
Additive scene
```

The key test:

> Does this module need its dependencies to be created and destroyed as one lifetime unit?

If yes → child scope.

If no → registration module inside an existing scope is enough.

---

# 15. VContainer Lifetime Selection

Use the shortest lifetime that correctly models ownership.

## `Lifetime.Singleton`

Use for one instance shared for the lifetime of its container.

Typical project-level examples:

```text
PlayerSession
AuthenticationService
Analytics
Backend client
SaveService
SceneLoader
AudioService
```

Do not use Singleton merely because:

> "I only need one."

Ask whether its lifetime is really application-wide.

---

## `Lifetime.Scoped`

Excellent default for feature/scene services.

Examples:

```text
ShopService
WardrobeService
MatchService
MatchState
TournamentPresenter
SceneCoordinator
```

A child scope can own these and dispose of them together.

---

## `Lifetime.Transient`

Use when each resolve should get a new object.

Useful for genuinely short-lived objects or factories.

Do not use it as your default just because the type is lightweight.

---

# 16. VContainer Entry Points

VContainer can run plain C# classes through its PlayerLoop integration.

Example:

```csharp
public sealed class ShopPresenter : IStartable, IDisposable
{
    private readonly ShopView _view;
    private readonly ShopService _shop;

    public ShopPresenter(
        ShopView view,
        ShopService shop)
    {
        _view = view;
        _shop = shop;
    }

    public void Start()
    {
        _view.BuyPressed += OnBuyPressed;
        Refresh();
    }

    private void OnBuyPressed()
    {
        _shop.Buy(/* item */);
        Refresh();
    }

    private void Refresh()
    {
    }

    public void Dispose()
    {
        _view.BuyPressed -= OnBuyPressed;
    }
}
```

Registration:

```csharp
builder.RegisterEntryPoint<ShopPresenter>();
```

This is a great fit for Presenters, coordinators, and application startup logic.

It lets many orchestration classes remain plain C# instead of becoming MonoBehaviours only to receive `Start()` or `Update()`.

---

# 17. Do Not Inject the Container Everywhere

Avoid:

```csharp
public class ShopService
{
    private readonly IObjectResolver _container;

    public ShopService(IObjectResolver container)
    {
        _container = container;
    }

    public void Buy()
    {
        var inventory = _container.Resolve<InventoryService>();
    }
}
```

That is the **Service Locator** pattern hiding inside your DI container.

It defeats much of the benefit of DI.

Prefer:

```csharp
public ShopService(InventoryService inventory)
{
    _inventory = inventory;
}
```

Use the container in:

```text
Composition Roots
Factories that genuinely require runtime construction
special framework glue
```

not in ordinary business code.

---

# 18. Constructor Injection Is the Default

For plain C#:

```csharp
public ShopService(
    IPlayerRepository players,
    IAnalytics analytics)
{
}
```

Prefer constructor injection.

For Unity components, serialized fields are still completely valid for **Unity object references**:

```csharp
public sealed class ShopView : MonoBehaviour
{
    [SerializeField] Button buyButton;
    [SerializeField] TMP_Text price;
}
```

You do not need DI for every Button and Transform.

A useful division:

```text
Unity object graph
    → SerializeField

software/service dependency graph
    → VContainer
```

That is very pragmatic.

---

# 19. Presenter or Controller?

Do not become religious about naming.

Use a Presenter when you have:

```text
View
  ↓ input
Presenter
  ↓
Application
  ↑ result/state
Presenter
  ↓
View
```

For gameplay components, `Controller` may be clearer.

Example:

```text
PlayerInputView
      ↓
PlayerController
      ↓
Movement / Gameplay Service
```

The important thing is responsibility, not suffixes.

---

# 20. Application Service vs Dedicated Use Case

Do not create one class per verb automatically.

Default:

```csharp
public sealed class WardrobeService
{
    public void Equip(ItemId id) { }
    public void Unequip(OutfitSlot slot) { }
    public void Preview(ItemId id) { }
}
```

This is a cohesive feature API.

---

## Extract a dedicated Use Case when the workflow becomes significant

Example:

```text
PurchaseItemUseCase
```

because it may coordinate:

```text
Offer validation
     ↓
Wallet
     ↓
Inventory
     ↓
Mission progress
     ↓
Persistence
     ↓
Analytics
```

Rule:

> **Application Service for cohesive everyday feature operations. Dedicated Use Case for an important workflow that deserves its own identity.**

---

# 21. Cross-Module Communication

Avoid:

```text
Wardrobe
   ↓
InventoryService concrete implementation
```

if the dependency becomes a hard feature coupling.

Prefer a narrow capability.

Example owned by the consumer:

```csharp
public interface IOwnedItemLookup
{
    bool IsOwned(ItemId id);
}
```

Wardrobe:

```csharp
public sealed class WardrobeService
{
    private readonly IOwnedItemLookup _ownedItems;

    public WardrobeService(IOwnedItemLookup ownedItems)
    {
        _ownedItems = ownedItems;
    }
}
```

Inventory can provide an adapter:

```csharp
public sealed class InventoryOwnedItemLookup
    : IOwnedItemLookup
{
}
```

This follows the **Dependency Inversion Principle**:

> High-level code states what capability it needs. Outer/concrete code satisfies that capability.

---

# 22. Do Not Put Every Interface in `Core`

This tends to create:

```text
Core/
├── IShopService
├── IInventoryService
├── IWardrobeService
├── IMissionService
├── ITournamentService
└── ...
```

Eventually `Core` knows the entire game.

Instead:

- keep feature-specific contracts near the feature/consumer that owns the requirement
- keep genuinely universal abstractions in Shared/Core

Good global/shared abstractions:

```text
IClock
IAnalytics
ISaveService
IRandom
ILogger
INetworkConnection
```

Not every feature API belongs globally.

---

# 23. Events: When to Use Them

Events are excellent when one thing happens and multiple independent systems care.

Example:

```text
PurchaseCompleted
      │
      ├── Mission tracking
      ├── Analytics
      ├── UI notification
      └── Tutorial progression
```

This avoids:

```csharp
shopService.NotifyMission();
shopService.NotifyAnalytics();
shopService.NotifyTutorial();
shopService.NotifyHud();
```

But avoid turning your entire project into an invisible global event bus.

Prefer:

- direct dependency when there is one obvious collaborator
- events when multiple independent observers genuinely react

---

# 24. ScriptableObjects

Use ScriptableObjects primarily for Unity-authored configuration.

```csharp
[CreateAssetMenu]
public sealed class ClubDefinition : ScriptableObject
{
    public string Id;
    public float Power;
    public int UpgradeCost;
}
```

Runtime state:

```csharp
public sealed class OwnedClub
{
    public ClubId Id { get; }
    public int Level { get; private set; }
}
```

Think:

```text
ScriptableObject
"What is this thing?"

Runtime domain model
"What is this player's current state for this thing?"
```

Avoid putting mutable player save state directly into asset ScriptableObjects unless you intentionally want asset-backed runtime state and fully understand the lifecycle implications.

---

# 25. Gameplay Hot Paths

Clean Architecture is not a requirement for every frame.

Do not turn:

```csharp
void FixedUpdate()
```

into:

```text
MonoBehaviour
   ↓
Presenter
   ↓
UseCase
   ↓
Repository
   ↓
DomainService
```

for no reason.

For hot gameplay code a short dependency path is often ideal:

```text
GolfSwingController : MonoBehaviour
        │
        ▼
ShotCalculator : C#
        │
        ▼
ShotRules : C#
```

Unity owns physics.

Plain C# owns calculations/rules when that separation gives value.

---

# 26. Example: Complete Shop Module

```text
Shop/
│
├── Domain/
│   ├── ShopItem.cs
│   ├── Price.cs
│   └── PurchaseResult.cs
│
├── Application/
│   ├── ShopService.cs
│   └── PurchaseItemUseCase.cs      // only if workflow warrants it
│
├── Presentation/
│   ├── ShopView.cs                 // MonoBehaviour
│   ├── ShopItemView.cs             // MonoBehaviour
│   └── ShopPresenter.cs            // plain C#
│
├── Infrastructure/
│   └── RemoteShopCatalog.cs        // if Shop owns remote data access
│
└── Composition/
    └── ShopComposition.cs
```

Flow:

```text
┌──────────────┐
│   ShopView   │ MonoBehaviour
└──────┬───────┘
       │ button
       ▼
┌──────────────┐
│ShopPresenter │ plain C#
└──────┬───────┘
       │
       ▼
┌──────────────┐
│ ShopService  │ Application
└──────┬───────┘
       │
       ├───────────────┐
       ▼               ▼
   Player/Wallet    ShopItem
      Domain         Domain
       │
       ▼
IPlayerRepository
       ▲
       │
NakamaPlayerRepository
 Infrastructure
```

---

# 27. Example: Gameplay Module

```text
Gameplay/
│
├── Domain/
│   ├── ShotInput.cs
│   ├── ShotResult.cs
│   ├── ShotCalculator.cs
│   └── ScoringRules.cs
│
├── Application/
│   ├── MatchService.cs
│   └── CompleteHoleUseCase.cs
│
├── Presentation/
│   ├── GolfBallBody.cs
│   ├── PlayerInput.cs
│   ├── ShotHudView.cs
│   └── MatchPresenter.cs
│
└── Composition/
    └── GameplayComposition.cs
```

A Rigidbody does not need a repository, presenter, or interface merely because you use Clean Architecture.

---

# 28. Persistent Data Example

Recommended flow:

```text
LOGIN / BOOT
    │
    ▼
LoadPlayerUseCase
    │
    ▼
IPlayerRepository
    │
    ▼
NakamaPlayerRepository
    │
    ▼
PlayerProfile
    │
    ▼
PlayerSession.SetProfile()
```

During gameplay:

```text
ShopService
     │
     ▼
PlayerSession.Profile.Wallet
```

When persistence is required:

```text
ShopService / Save coordinator
     │
     ▼
IPlayerRepository.Save(profile)
```

This avoids treating persistence storage as your live object graph.

---

# 29. One Root + Scene Roots + Optional Child Feature Roots

This is the recommended composition structure:

```text
ProjectLifetimeScope
│
│  long-lived dependencies
│
├────────────────────────────────────────────┐
│                                            │
▼                                            ▼
MainMenuLifetimeScope                 GameplayLifetimeScope
│                                            │
│ ShopComposition                            │ GameplayComposition
│ WardrobeComposition                        │ HUDComposition
│ InventoryComposition                       │ MatchComposition
│                                            │
│                                            ▼
│                                  Optional MatchLifetimeScope
│                                  created for one match only
│
▼
disposed when scene/flow ends
```

### Guideline

**Project root**
- only application-wide systems

**Scene root**
- dependencies owned by that loaded scene / major flow

**Module composition**
- registration methods that keep feature wiring with the feature

**Child LifetimeScope**
- only when the feature has a distinct create/dispose lifetime

---

# 30. What Should Be a Singleton?

Do not ask:

> "Will there only be one?"

Ask:

> "Who owns this instance, and how long should it live?"

Reasonable application-scope candidates:

```text
AuthenticationSession
PlayerSession
BackendConnection
Analytics
SaveService
SceneLoader
AudioService
RemoteConfig cache
```

Often **not** application singletons:

```text
ShopPresenter
MatchService
HUDController
CurrentMatchState
PopupPresenter
LevelController
EnemySpawner
```

Those belong to smaller scopes.

---

# 31. Global Static Singleton vs VContainer Singleton

These are very different.

Avoid:

```csharp
GameManager.Instance
InventoryManager.Instance
SaveManager.Instance
```

Prefer:

```csharp
builder.Register<SaveService>(Lifetime.Singleton);
```

then:

```csharp
public Foo(SaveService save)
{
}
```

Advantages:

- dependencies are visible
- tests can substitute dependencies
- lifetimes are explicit
- fewer initialization-order problems
- scope disposal is possible
- no global static access

---

# 32. Design Patterns You Should Know

These are the patterns most relevant to this architecture.

## Tier 1 — Must Understand

### Dependency Injection
Learn:
- constructor injection
- composition root
- object graph
- dependency lifetime
- avoiding Service Locator

Used everywhere with VContainer.

---

### Dependency Inversion Principle
Learn:

```text
high-level policy
      ↓
   interface
      ↑
low-level implementation
```

Essential for backend, save, analytics, payment, cross-module boundaries.

---

### Repository
Use for meaningful data persistence/retrieval.

Learn:
- repository vs runtime state
- repository vs service
- async repositories

---

### Adapter
Wrap external APIs.

Examples:

```text
IAnalytics ← AdjustAdapter
IPaymentGateway ← UnityIAPAdapter
IPlayerRepository ← NakamaPlayerRepository
```

---

### Observer / Events
Use for independent reactions to state changes.

Learn:
- C# events
- event channels carefully
- subscription lifetime
- avoiding global event-bus abuse

---

### State Pattern / Finite State Machine
Extremely useful for gameplay and flows.

Examples:

```text
Match
Loading → Ready → Playing → Results

Character
Idle → Aiming → Swinging → Recovering
```

---

# 33. Tier 2 — Very Useful

### Strategy
Swap algorithms/behavior.

```text
IShotModifier
├── NormalShot
├── PowerShot
└── PrecisionShot
```

---

### Factory
Use when construction needs runtime parameters or becomes complex.

Particularly useful with VContainer when objects are spawned dynamically.

Learn:
- factory responsibility
- prefab factories
- DI-assisted construction

---

### Command
Useful for:
- input actions
- queued actions
- undo
- replay
- turn-based systems

---

### Facade
Expose a simple API over a complex subsystem.

Example:

```text
CommerceFacade
  ├── IAP
  ├── wallet
  ├── inventory
  └── analytics
```

Use carefully; do not turn facades into God objects.

---

### Presenter / MVP
Useful for non-trivial UI.

Learn:
- passive View
- Presenter orchestration
- view events
- Presenter disposal/subscription cleanup

---

# 34. Tier 3 — Learn as Needed

- Decorator
- Composite
- Specification
- Mediator
- Chain of Responsibility
- Object Pool
- Flyweight
- Reactive programming
- CQRS

Do not force these into the project because a pattern list says so.

---

# 35. SOLID: Which Parts Matter Most?

Learn all five, but emphasize:

## S — Single Responsibility

A class should have one coherent reason to change.

Not:

```text
PlayerManager
- saves player
- controls UI
- calculates XP
- sends analytics
- loads scenes
```

---

## O — Open/Closed

Useful when behaviors vary, but don't abstract prematurely.

---

## L — Liskov Substitution

Understand it primarily when building polymorphic interfaces/base classes.

---

## I — Interface Segregation

Very important for module boundaries.

Prefer:

```csharp
IOwnedItemLookup
```

over:

```csharp
IInventoryEverythingService
```

---

## D — Dependency Inversion

Most important for this architecture.

High-level features shouldn't depend directly on Nakama, JSON, Firebase, etc.

---

# 36. Topics Worth Learning/Revising

Use this as your study list.

## Architecture
- Clean Architecture dependency rule
- vertical slice / feature-based architecture
- cohesion vs coupling
- boundaries
- composition root
- modular monolith concepts

## Dependency Injection
- constructor injection
- object graphs
- VContainer LifetimeScope
- parent/child scopes
- scoped vs singleton vs transient
- entry points
- disposal
- factories
- avoiding Service Locator

## Domain Modeling
- entity
- value object
- invariant
- domain service
- rich model vs anemic model
- aggregate **only when your project actually needs the concept**

Do not jump directly into full Domain-Driven Design.

## Application Layer
- orchestration
- use cases
- application services
- commands/results
- transaction/workflow boundaries

## Persistence
- repository pattern
- DTO vs domain model
- serialization boundaries
- runtime state vs saved state
- mapping

## Unity
- MonoBehaviour lifecycle
- ScriptableObject lifetime
- additive scene loading
- scene ownership
- Unity serialization
- Addressables lifetime
- object pooling
- event subscription lifetime

## Testing
- unit tests for Domain
- unit tests for Application
- fake repositories/adapters
- integration tests for Infrastructure
- Unity PlayMode tests only where Unity behavior must be exercised

---

# 37. Testing Strategy

Architecture earns its keep when important code becomes easy to test.

## Domain

```csharp
[Test]
public void Wallet_CannotSpendMoreThanBalance()
{
    var wallet = new Wallet(100);

    Assert.Throws<InvalidOperationException>(
        () => wallet.Spend(150));
}
```

No scene required.

---

## Application

```csharp
[Test]
public void Purchase_GrantsItem_WhenAffordable()
{
    var repository = new FakePlayerRepository();
    var catalog = new FakeShopCatalog();

    var shop = new ShopService(repository, catalog);

    var result = shop.Buy(ItemIds.Shoes);

    Assert.AreEqual(PurchaseResult.Success, result);
}
```

No GameObject required.

---

## Presentation

Test selectively.

Don't spend huge effort unit testing thin views whose job is simply:

```text
set text
show panel
raise button event
```

---

# 38. Common Architecture Smells

If you see these, reconsider.

### Smell 1

```text
Manager.Instance
```

everywhere.

---

### Smell 2

Every operation has:

```text
Interface
Implementation
UseCase
Presenter
Repository
Factory
```

despite being trivial.

---

### Smell 3

`Core` knows every feature.

---

### Smell 4

Application classes use:

```text
GameObject
Transform
TMP_Text
Button
Animator
```

without a strong reason.

---

### Smell 5

Domain knows:

```text
Nakama
Firebase
JSON
PlayerPrefs
UnityEngine.UI
```

---

### Smell 6

Every system injects:

```csharp
IObjectResolver
```

and resolves dependencies manually.

That is Service Locator.

---

### Smell 7

A repository is used merely to access an in-memory singleton.

---

### Smell 8

There is one enormous:

```text
GameManager
GameService
AppController
```

coordinating the entire project.

---

### Smell 9

An event bus makes it impossible to tell what calls what.

---

### Smell 10

You need five new files before implementing a two-line feature.

---

# 39. The Pragmatic Complexity Ladder

## Level 1 — Tiny feature

```text
MonoBehaviour
```

Enough.

---

## Level 2 — Simple logic

```text
MonoBehaviour
     ↓
Plain C# service/model
```

---

## Level 3 — Normal production feature

```text
View
 ↓
Presenter / Controller
 ↓
Application Service
 ↓
Domain
```

This should be your most common architecture.

---

## Level 4 — Important workflow

```text
View
 ↓
Presenter
 ↓
Dedicated Use Case
 ↓
Domain
 ↓
Repository / external ports
```

---

## Level 5 — External technology

```text
Application
     ↓
Interface
     ↑
Adapter
     ↓
SDK / Backend
```

Be strict here.

---

# 40. Final Decision Table

| Situation | Default choice |
|---|---|
| Button / TMP / Canvas / UI animation | Presentation MonoBehaviour |
| Rigidbody / Collider / Animator | Feature Unity/Presentation component |
| Nakama / Firebase / Adjust / IAP | Infrastructure Adapter |
| Player's in-memory current profile | Plain C# session object |
| Saved player data | Repository |
| App-wide session/service | Project LifetimeScope Singleton |
| Scene-specific service | Scene LifetimeScope Scoped |
| Match-only service | Match child LifetimeScope Scoped |
| Designer-authored config | ScriptableObject |
| Fundamental game rule | Domain |
| Coordinates feature workflow | Application Service |
| Large important workflow | Dedicated Use Case |
| Cross-feature requirement | Narrow consumer-owned interface |
| Unity object references | `[SerializeField]` |
| software/service dependencies | VContainer injection |
| Runtime creation is complex | Factory |
| Many independent listeners | Event / Observer |
| Changing behavior | Strategy |
| Gameplay phase changes | State Machine |

---

# 41. Recommended Rules for Your Team

If you remember nothing else, enforce these.

1. **Organize by feature first.**

2. **Domain contains meaningful game rules and state, not every data class.**

3. **Application coordinates workflows; it should not care how Unity draws things or how an SDK works.**

4. **MonoBehaviours are allowed. Classify them by responsibility, not by inheritance.**

5. **Keep important runtime state in plain C# objects registered with the correct VContainer lifetime. Avoid static singleton access.**

6. **Repositories represent persistence/data sources—not universal access to runtime state.**

7. **Wrap external SDKs and backend technology behind interfaces/adapters.**

8. **Use VContainer constructor injection for service dependencies; use SerializeField for Unity object references.**

9. **Keep one application root, scene roots for major flows, and child scopes only when something has a real independent lifetime.**

10. **Keep module registration with the module, but don't create a LifetimeScope GameObject for every module.**

11. **Application Services are the default; create separate Use Case classes only for substantial workflows.**

12. **Prefer direct dependencies over a global event bus. Use events when multiple independent systems genuinely react.**

13. **Never inject `IObjectResolver` everywhere.**

14. **Use the shortest VContainer lifetime that correctly models ownership.**

15. **Do not abstract Unity away merely to claim architectural purity.**

16. **Do abstract business rules and external technology when doing so makes change/testing easier.**

17. **If architecture makes a simple change dramatically harder, simplify it.**

---

# 42. The 30-Second Mental Checklist

Before writing a new feature:

```text
1. Which FEATURE owns this?
        ↓
2. Is there an actual GAME RULE?
        ├─ yes → Domain
        └─ no
        ↓
3. Is there an actual WORKFLOW?
        ├─ yes → Application
        └─ no
        ↓
4. Does Unity display/control it?
        ├─ yes → Presentation / Unity component
        ↓
5. Does it talk to SDK/storage/network?
        ├─ yes → Infrastructure
        ↓
6. Who OWNS its lifetime?
        ├─ app   → ProjectLifetimeScope
        ├─ scene → SceneLifetimeScope
        └─ flow  → Child LifetimeScope
        ↓
7. Does another module need it?
        └─ expose the smallest useful contract
```

---

# 43. Final Architecture Philosophy

The goal is **not**:

```text
Clean Architecture everywhere.
```

The goal is:

```text
Put boundaries where change is expensive.
Keep Unity where Unity is useful.
Keep rules testable.
Keep dependencies visible.
Keep lifetimes explicit.
Keep features cohesive.
```

Or, in one line:

> **Feature-first Unity architecture, plain-C# rules and workflows where valuable, external technology behind adapters, and VContainer as the explicit lifetime/composition system.**

That is the architecture to keep using until a concrete project problem gives you a reason to evolve it.

---

# Sources and Basis

This guide synthesizes the two architecture discussions supplied for this task:

- `Chatgpt Unity Architecture.md` — Clean Architecture mental model, View/Presenter/Use Case/Domain separation, consumer-oriented interfaces, repositories/services, ScriptableObjects, patterns, and manual composition root guidance.
- `Google Unity Architecture.md` — vertical feature modules, Domain/Application/Presentation/Infrastructure organization, application services as a pragmatic alternative to one-class-per-use-case, and modular composition guidance.

VContainer-specific recommendations were checked against the current official VContainer documentation, particularly:

- `LifetimeScope`
- parent/child scopes
- `Lifetime.Singleton`, scoped registrations, and registration examples
- `RegisterEntryPoint`
- pure-C# PlayerLoop entry points
- dynamically created child scopes
- additive-scene scope parenting

Official documentation: https://vcontainer.hadashikick.jp/

---

## Recommended next study order

```text
1. Dependency Injection + Composition Root
2. VContainer LifetimeScope and lifetimes
3. SOLID: SRP, ISP, DIP
4. Domain rule vs Application workflow
5. Repository + Adapter
6. MVP / Presenter
7. Observer / Events
8. State Machine
9. Strategy
10. Factory
```

Do not try to master all of DDD before using this architecture. Learn richer domain-model concepts gradually as your game rules become complex enough to need them.


---

# ⭐ Architecture Clarifications (Refined)

## Module Communication ≠ Infrastructure

Infrastructure is for **external technology** (Nakama, Firebase, JSON, PlayerPrefs, Analytics SDKs, Ads, IAP, REST APIs).

Communication between your own modules is **not automatically Infrastructure**.

Example:

```text
Wardrobe
    │
needs ownership information
    ▼
IOwnedItemLookup
    ▲
InventoryOwnedItemLookup
    ▲
InventoryService
```

This is an **integration boundary**, not an infrastructure boundary.

If useful, introduce an optional folder:

```text
Feature/
├── Domain/
├── Application/
├── Unity/ (or Presentation/)
├── Integration/
├── Infrastructure/
└── Composition/
```

- **Integration** = adapters between your own modules.
- **Infrastructure** = adapters to external technology.

---

## MonoBehaviour Is Not an Architecture Layer

`MonoBehaviour` only means Unity owns the object's lifecycle.

Examples:

**Unity / Presentation**

- PlayerController
- PlayerInput
- PlayerAnimator
- ShopView
- HUDView
- BallBody

**Infrastructure**

- NakamaAdapter
- FirebaseAnalyticsAdapter
- UnityIAPAdapter
- CloudSaveComponent

Classify by responsibility, not inheritance.

---

## Player Module Example

```text
Player/
├── Domain/
│   ├── PlayerState.cs
│   ├── PlayerStats.cs
│   └── MovementRules.cs
├── Application/
│   ├── PlayerMovementService.cs
│   └── RespawnPlayerUseCase.cs
├── Unity/
│   ├── PlayerController.cs
│   ├── PlayerInput.cs
│   └── PlayerAnimator.cs
├── Integration/
│   └── PlayerLevelProvider.cs
├── Infrastructure/
│   └── NakamaPlayerRepository.cs
└── Composition/
```

---

## Interfaces

Don't create interfaces automatically.

Create them when:

- another feature depends on a capability
- multiple implementations exist
- isolating infrastructure
- creating a dependency boundary

Avoid `IPlayerMovementService` unless it solves a real problem.

---

## Runtime State vs Repository

```text
Gameplay
    │
    ▼
PlayerSession
    │
    └── runtime state
    │
    ▼
IPlayerRepository
    │
    ▼
Nakama / JSON / Cloud
```

Repositories persist data.

Sessions own runtime state.

---

## SerializeField vs VContainer

```text
Unity references
    ↓
[SerializeField]

Software dependencies
    ↓
Constructor / [Inject]
```

Use SerializeField for Buttons, TMP, Rigidbody, Animator.

Use VContainer for services, repositories, sessions, analytics, networking.

---

## Final Decision Tree

```text
Rule?
    → Domain

Workflow?
    → Application

Unity object?
    → Unity / Presentation

Internal module integration?
    → Integration

External technology?
    → Infrastructure

Who owns its lifetime?
    → Composition (VContainer)
```
