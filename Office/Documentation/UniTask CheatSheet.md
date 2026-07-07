# Coroutine → UniTask Cheat Sheet

A quick reference guide for converting Unity Coroutines into UniTask equivalents.

---

## 🔹 Time-based Waiting

| Coroutine | UniTask Equivalent |
|-----------|---------------------|
| `yield return new WaitForSeconds(1f);` | `await UniTask.Delay(TimeSpan.FromSeconds(1));` |
| `yield return new WaitForSecondsRealtime(1f);` | `await UniTask.Delay(TimeSpan.FromSeconds(1), DelayType.Realtime);` |

---

## 🔹 Frame-based Waiting

| Coroutine | UniTask Equivalent |
|-----------|---------------------|
| `yield return null; // next frame` | `await UniTask.Yield();` |
| `yield return new WaitForFixedUpdate();` | `await UniTask.WaitForFixedUpdate();` |
| `yield return new WaitForEndOfFrame();` | `await UniTask.WaitForEndOfFrame();` |

---

## 🔹 Condition-based Waiting

| Coroutine | UniTask Equivalent |
|-----------|---------------------|
| `yield return new WaitUntil(() => isReady);` | `await UniTask.WaitUntil(() => isReady);` |
| `yield return new WaitWhile(() => isBusy);` | `await UniTask.WaitWhile(() => isBusy);` |

---

## 🔹 Fire-and-Forget

| Coroutine | UniTask Equivalent |
|-----------|---------------------|
| `StartCoroutine(SomeCoroutine());` | `SomeAsync().Forget();` |
| *(no need to yield)* | `SomeAsync(); // but ignore warning, or use .Forget()` |

---

## 🔹 Returning Values

**Coroutine (callback style):**
```csharp
IEnumerator GetValue(Action<int> callback)
{
    yield return new WaitForSeconds(1);
    callback(42);
}
```

**UniTask (async/await style):**
```csharp
async UniTask<int> GetValueAsync()
{
    await UniTask.Delay(1000);
    return 42;
}
```

---

## 🔹 Cancellation

**Coroutine (manual stop):**
```csharp
Coroutine routine;

void Start() {
    routine = StartCoroutine(MyRoutine());
}

void Stop() {
    StopCoroutine(routine);
}
```

**UniTask (cancellation token):**
```csharp
CancellationTokenSource cts = new CancellationTokenSource();

async UniTask MyTask(CancellationToken token)
{
    await UniTask.Delay(5000, cancellationToken: token);
}

void Start()
{
    MyTask(cts.Token).Forget();
}

void Stop()
{
    cts.Cancel();
}
```

---

## 🔹 Exceptions

**Coroutine:** exceptions are swallowed unless logged manually.  

**UniTask:** exceptions bubble up naturally with try/catch.  
```csharp
try
{
    await MyFailingTask();
}
catch (Exception ex)
{
    Debug.LogError(ex);
}
```

---

✅ **Rule of Thumb:** If you ever write `IEnumerator` in Unity, there’s almost always a **cleaner UniTask equivalent**.
