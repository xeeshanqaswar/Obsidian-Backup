
# 🎯 **1. LifetimeScopes — The HEART of VContainer**

The **LifetimeScope** is where you _register_ dependencies.

### ⭐ What it is

A container that controls:

- What objects exist
- How long they live (singleton/scoped)
- How they get injected

### ⭐ Why it matters

You can keep things organized:

- Global systems at app root
    
- Scene systems in scene scope
    
- UI windows in prefab scopes
    

### ⭐ Example

### **RootLifetimeScope**

Create this in your initial scene:

`public class AppLifetimeScope : LifetimeScope 
 {     
	protected override void Configure(IContainerBuilder builder)     
	{         
		builder.Register<SaveService>(Lifetime.Singleton);         builder.Register<GameManager>(Lifetime.Singleton);
	} 
}`

Now any scene or prefab can inject `SaveService` or `GameManager`.

---

# 🎯 **2. Basic Registration & Constructor Injection**

### ⭐ What it is

Registering classes so VContainer can construct them and inject dependencies.

### ⭐ Why it matters

You avoid `FindObjectOfType`, `new` in MonoBehaviours, and spaghetti singletons.

### ⭐ Example

`public class PlayerService {  
	  private readonly IInputService _input;
	  public PlayerService(IInputService input)    
	   {
		_input = input;
	}
 }`

Register both:

`builder.Register<IInputService, InputService>(Lifetime.Singleton); builder.Register<PlayerService>(Lifetime.Singleton);`

Now PlayerService automatically receives InputService.

---

# 🎯 **3. Injecting into MonoBehaviour**

### ⭐ What it is

You can have VContainer inject fields in Unity components.

### ⭐ Why it matters

MonoBehaviours can depend on services without manually wiring.

### ⭐ Example

`public class PlayerController : MonoBehaviour 
{ 
	   [Inject] private PlayerService playerService;
	   private void Start()     
	  {         
		playerService.Move();
	   } 
}`

Register the component:

`builder.RegisterComponentInHierarchy<PlayerController>();`

---

# 🎯 **4. Prefab Injection — SUPER IMPORTANT**

### ⭐ What it is

VContainer injects dependencies inside a prefab _when you instantiate it_.

### ⭐ Why it matters

No more manually doing:

- `GetComponent<Player>`
    
- drag-dropping references everywhere
    
- factories for objects
    

### ⭐ Example

Suppose you have a prefab `Enemy.prefab`:

`public class Enemy : MonoBehaviour {     [Inject] private IHealthService health; }`

Register the prefab:

`builder.RegisterComponentInNewPrefab(enemyPrefab, Lifetime.Transient);`

Instantiate it through VContainer:

`var enemy = container.Instantiate(enemyPrefab);`

HealthService gets injected automatically.

---

# 🎯 **5. ScriptableObject Injection**

### ⭐ What it is

Use ScriptableObjects as configuration or static data.

### ⭐ Why it matters

Clean approach for data-driven design.

### ⭐ Example

`[CreateAssetMenu] public class PlayerConfig : ScriptableObject {     public float speed; }`

Register:

`builder.RegisterInstance(playerConfig);`

Inject into class:

`public class PlayerService {     private readonly PlayerConfig config;      public PlayerService(PlayerConfig config)     {         this.config = config;     } }`

---

# 🎯 **6. Scopes (Scene Scope, UI Scope, Prefab Scope)**

### ⭐ What it is

Smaller containers under your main lifetime scope.

### ⭐ Why it matters

Essential when you have:

- Scene → Gameplay scope
    
- UI window → Popup scope
    
- Minigame mode → Isolated scope
    

### ⭐ Example: SceneLifetimeScope

Your Gameplay scene:

`public class GameplayScope : LifetimeScope {     protected override void Configure(IContainerBuilder builder)     {         builder.Register<ScoreService>(Lifetime.Scoped);     } }`

`ScoreService` lives only during this scene.

---

# 🎯 **7. GameLoop Interfaces (IInitializable, ITickable)**

### ⭐ What it is

Lets you write non-MonoBehaviour game logic.

### ⭐ Why it matters

Cleaner than Update loops inside MonoBehaviours.

### ⭐ Example

`public class GameLoop : ITickable, IInitializable {     public void Initialize()      {         Debug.Log("Game initialized");     }      public void Tick()     {         Debug.Log("Game update");     } }`

Register:

`builder.Register<GameLoop>(Lifetime.Singleton)        .As<IInitializable>()        .As<ITickable>();`

Now GameLoop runs automatically.

---

# 🎯 **8. Factories (for prefabs or pure C# classes)**

### ⭐ What it is

You can manually create objects but still have injection.

### ⭐ Example

### **Factory for a C# class**

`public class BulletFactory {     private readonly IObjectResolver container;      public BulletFactory(IObjectResolver container)     {         this.container = container;     }      public Bullet Create()     {         return container.Resolve<Bullet>();     } }`

Register:

`builder.Register<Bullet>(Lifetime.Transient); builder.Register<BulletFactory>(Lifetime.Singleton);`

---

# 🎯 **9. Async Initialization**

### ⭐ What it is

Support for `UniTask` and async setup.

### ⭐ Why it matters

Loading screens, async services, data loading.

### ⭐ Example

`public class SaveService : IAsyncStartable {     public async UniTask StartAsync()     {         await LoadFromDisk();     } }`

Register:

`builder.Register<SaveService>(Lifetime.Singleton)        .As<IAsyncStartable>();`

---

# 🎯 **10. Interface Binding (Most Common)**

### ⭐ What it is

Bind an interface to a class.

### ⭐ Why it matters

You can swap implementations (mocking/testing).

### ⭐ Example

`public interface IWeapon { } public class Sword : IWeapon { } public class Gun : IWeapon { }`

Register:

`builder.Register<IWeapon, Sword>(Lifetime.Singleton);`

Swap at runtime or per scope.

---

# 🎯 **11. Resolving Dependencies Manually**

Sometimes you need manual resolve:

`var service = container.Resolve<PlayerService>();`

This should be rare but useful for debugging.

---

# 🎯 **12. Life-Cycle: Dispose & Cleanup**

Useful for objects that need cleanup.

### Example

`public class NetworkService : IDisposable {     public void Dispose()     {         Disconnect();     } }`

Registered with any lifetime except transient.

---

# 🎯 **13. Pre-Existing Scene Object Injection**

For objects already in scene:

`builder.RegisterComponentInHierarchy<UIRoot>();`