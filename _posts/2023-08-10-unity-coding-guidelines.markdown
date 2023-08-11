---
layout: single
title:  "Unity C# Guidelines"
date:   2023-08-10 11:09:59 +0100
categories: unity coding
---

The style guidelines and best practices for our engineering team at Prickly Bear when working with Unity C#.

1. [Style Conventions](#style-conventions)
2. [C# Guidelines](#csharp-guidelines)
3. [Unity Guidelines](#unity-guidelines)


<a name="style-conventions"></a>

# 1. Style Conventions

## 1.1: Classes use PascalCase

```csharp
public class MyClass : MonoBehaviour { }
```

## 1.2 Methods use PascalCase

```csharp
private void DoSomething()
```

## 1.3 Private fields use camelCase

```csharp
private int privateField;
```

## 1.4 Protected fields use camelCase

```csharp
protected int protectedField;
```

## 1.5 Public Fields: no convention as we don’t use them (see [2.16 Avoid public fields](#avoid-public))

## 1.6 Public Properties use PascalCase

```csharp
public int PublicField { get; private set; }
```

## 1.7 Namespaces use PascalCase

```csharp
namespace PricklyBear.SDK 
```

## 1.8 Parameters use camelCase

```csharp
public void GetRequestWithURL(bool showWaiting)
```

## 1.9  Prefix Events and Actions with **On**

```csharp
public Action OnTokenReady { get; private set; }
```

## 1.10 Interfaces start with an **I**

```csharp
public interface IGameService {}
```

## 1.11 Enums use PascalCase

```csharp
public enum Token 
{
  None,
  Up,
  Down,
  Left,
  Right
}
```

<a name="csharp-guidelines"></a>

# 2. C# Guidelines

## 2.1 Always use access level modifiers

**Always** **use access level modifiers**. Do not omit them. If you don’t write any access modifier, the compiler will assume it’s private, but that doesn’t mean you shouldn’t write the keyword private. Be mindful in our design. 

Instead of:

```csharp
bool isPrivate = true;

void PrivateMethod()
{
}
```

Do:

```csharp
private bool isPrivate = true;

private void PrivateMethod()
{
}
```

## 2.2 Use readonly modifier for fields that don’t change

```csharp
private readonly IServiceLocator serviceLocator = new ServiceLocator();
```

## 2.3 Use a single declaration per line

Instead of:

```csharp
private int firstVariable, secondVariable;
```

Do:

```csharp
private int firstVariable; 
private int secondVariable;
```

## 2.4 Use expression-bodied properties for **single-line, read-only properties**

```csharp
// read-only, returns backing field
public int MaxHealth => maxHealth;

// the private backing field
private int maxHealth;
```

## 2.5 Add fields before methods

Instead of:

```csharp
public bool PublicField;

public void SomeMethod()
{
}

protected bool protectedField;
private bool privateField;
```

Do:

```csharp
public bool PublicField;
protected bool protectedField;
private bool privateField;

public void SomeMethod()
{
}
```

## 2.6 Public fields come before protected fields. Protected fields come before private fields.

Instead of:

```csharp
private bool privateField;
public bool PublicField;
protected bool protectedField;
```

Do:

```csharp
public bool PublicField;
protected bool protectedField;
private bool privateField;
```

## 2.7 Public methods come before protected methods. Protected methods come before private methods.

Instead of

```csharp
private void PrivateMethod()
{
}

public void PublicMethod()
{
}

protected void ProtectedMethod()
{
}
```

Do:

```csharp
public void PublicMethod()
{
}

protected void ProtectedMethod()
{
}

private void PrivateMethod()
{
}
```

## 2.8 Add one vertical space between methods

Instead of:

```csharp
public void MethodOne()
{
}
public void MethodTwo()
{
}
```

Do:

```csharp
public void MethodOne()
{
}

public void MethodTwo()
{
}
```

## 2.9 Always use braces

Instead of:

```csharp
if(...)
  DoSomething();
```

Do:

```csharp
if(...)
{
  DoSomething();
}
```

## 2.10 Put braces on a new line

(sorry JS developers)

Instead of:

```csharp
if(...) {
}
```

Do:

```csharp
if(...)
{
}
```

## 2.11 Add horizontal spaces to decrease code density

Instead of:

```csharp
CollectItem(myObject,0,1);

for(inti=0;i<100;i++){DoSomething(i);}

if(x==y)
```

Do:

```csharp
CollectItem(myObject, 0, 1);

for (int i = 0; i < 100; i++) { DoSomething(i); }

if(x == y)
```

## 2.12 Remove spaces around parenthesis and square brackets

Instead of:

```csharp
DropPowerUp( myPrefab, 0, 1 );

DoSomething ();

x = dataArray[ index ];
```

Do:

```csharp
DropPowerUp(myPrefab, 0, 1);

DoSomething();

x = dataArray[index];
```

## 2.13 Indent switch cases

```csharp
switch (switchCase)
{
  case HandledDomains.PricklyAI:
    var levelID = deeplinkPath[1];
    Debug.Log("Load prickly ai level + " + levelID);
    break;

  case HandledDomains.Unknown:
    Debug.LogWarning("DeepLinkHandler: unhandled deeplink");
    break;
}
```

## 2.14 Ensure all cases are handled in a switch statement

Instead of:

```csharp
enum SwitchCases
{
  Unknown,
  DoOne,
  DoTwo
}

HandledDomains switchCase = HandledDomains.DoOne;

switch (switchCase)
{
  case HandledDomains.DoOne:
    break;

  case HandledDomains.Unknown:
    break;

  // Missing case HandledDomains.DoTwo
}
```

Do:

```csharp
enum SwitchCases
{
  Unknown,
  DoOne,
  DoTwo
}

HandledDomains switchCase = HandledDomains.DoOne;

switch (switchCase)
{
  case HandledDomains.DoOne:
    break;

  case HandledDomains.DoTwo:
    break;

  case HandledDomains.Unknown:
    break;
}
```

## 2.15 Don’t use strings for branching e.g. switch case value

Instead of:

```csharp
string switchCase = "PricklyAI";

switch (switchCase)
{
  case "PricklyAI":
    var levelID = deeplinkPath[1];
    Debug.Log("Load prickly ai level + " + levelID);
    break;

  case "Unknown":
    Debug.LogWarning("DeepLinkHandler: unhandled deeplink");
    break;
}
```

Do:

```csharp
enum HandledDomains
{
  Unknown,
  PricklyAI
}

HandledDomains switchCase = HandledDomains.PricklyAI;

switch (switchCase)
{
  case HandledDomains.PricklyAI:
    var levelID = deeplinkPath[1];
    Debug.Log("Load prickly ai level + " + levelID);
    break;

  case HandledDomains.Unknown:
    Debug.LogWarning("DeepLinkHandler: unhandled deeplink");
    break;
}
```

<a name="avoid-public"></a>

## 2.16 Avoid public fields

Public fields are generally a bad idea. They’re not encapsulated and it’s hard to tell why they’re public. Are they set in the inspector? Modified by another class? Avoid them. Use private variables whenever possible. 

If you need to access something publicly, make it a **property** with a **public** **getter:**

```csharp
public string MyStringThatNeedsPublicReading { get; private set; }
```

If you need a private variable, but want to set it in the inspector use **SerializeField** (on one line):

```csharp
[SerializeField] private UserAuthenticationToken authenticationToken;
```

## 2.17 Avoid public static fields and methods

Use private static, when you need class level data. 

Instead of:

```csharp
public static bool PublicStaticState = true;
```

The exception to this rule is event fields, where you can set public with properties: 

```csharp
public static Action OnEvent { get; set; }
```

## 2.18 Avoid large classes. A class should be responsible for 1 thing. Avoid ‘Manager’ classes that do 100 things in 1 domain.

Large classes are a nightmare to maintain and extend. Avoid them.

As a rough guide, if a class is reaching > 4**00** lines, it’s time to refactor. Remember the ‘S’ in Solid. A class should only be responsible for one thing,

## 2.19 Avoid large methods. A method should do 1 thing.

As with large classes, large methods make code resistant to change. Aim to keep function length to < **15 lines**.

## 2.20 Use [Guard Clauses](https://deviq.com/design-patterns/guard-clause)

Instead of:

```csharp
if(userInDB)
{
  if(userAuthorised)
  {
    // User is authorised
  }
}
```

Do:

```csharp
if(!userInDB && !userAuthorised)
{
  return;
}

// User is authorised
```

## 2.21 All code should live in a namespace

Instead of:

```csharp
public interface IGameService
{
}
```

Do:

```csharp
namespace PricklyBear.SDK
{
  public interface IGameService
  {
  }
}
```

## 2.22 Do not commit commented code

Instead of:

```csharp
private void SetRandomColor()
{
  //Color randomColor = backgroundColors[Random.Range(0, backgroundColors.Length)];
  Sprite bg_sprite = backgroundColors[Random.Range(0, backgroundColors.Length)];
  //PlayerPrefs.SetString("LastBackgroundColor", randomColor.ToString());
  //PlayerPrefs.SetString("LastBackgroundColor", bg_sprite.ToString());
  this.gameObject.GetComponent<Image>().sprite = bg_sprite;
  // LeanTween.value(gameObject, UpdateBackgroundColor, mainCamera.backgroundColor, randomColor, 1);
}
```

Do:

```csharp
private void SetRandomColor()
{
  Sprite bg_sprite = backgroundColors[Random.Range(0, backgroundColors.Length)];
  this.gameObject.GetComponent<Image>().sprite = bg_sprite;
}
```

## 2.23 Do Not Commit Empty Methods

Especially Unity events. There is a small overhead to having an empty Unity event function.

## 2.24 Ensure all imports are used

They can safely be removed if greyed out in Visual Studio.
## 2.25 Add a TODO comment when further work is required but is not currently in scope

```csharp
//TODO: Add check for edge case X
```

## 2.26 Use [string interpolation](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/tokens/interpolated) to concatenate short strings.

```csharp
string firstName = "Rob";
string lastName = "Wells";
string userName = $"{firstName}, {lastName}";
string username = firstname + ", " + lastname;
```

## 2.27 Use [StringBuilder](https://learn.microsoft.com/en-us/dotnet/api/system.text.stringbuilder) when appending large number of text

```csharp
var phrase = "Hello World";
var manyPhrases = new StringBuilder();
for (var i = 0; i < 10000; i++)
{
  manyPhrases.Append(phrase);
}
```

## 2.28 Only use Implicit typing when the type is obvious

Instead of:

```csharp
var type = MethodThatReturnsSomething();
```

Do:

```csharp
string type = MethodThatReturnsSomething();
var typeObvious = true;
```

## 2.29 Use int rather than unsigned types

The use of int common throughout C#, and it is easier to interact with other libraries when you it.

## 2.30 Use the concise form of object initialisation

Instead of:

```csharp
ExampleClass instance1 = new ExampleClass();
```

Do:

```csharp
// Either acceptable
var instance1 = new ExampleClass();
ExampleClass instance2 = new();
```

## 2.31 Use object initialisers to simplify object creation

```csharp
var instance1 = new ExampleClass { Name = "Hello", ID = 37414 };
```

## 2.32 Program to interface not implementation

Reduce tightly coupled code makes changes easier.

Instead of:

```csharp
public class ServiceLocator 
{
...       
}

public class ServiceLocatorComp : MonoBehaviour
{
  private readonly ServiceLocator serviceLocator = new();
}
```

Do:

```csharp
public class ServiceLocator : IServiceLocator
{
...       
}

public class ServiceLocatorComp : MonoBehaviour
{
  private readonly IServiceLocator serviceLocator = new ServiceLocator();
}
```

<a name="unity-guidelines"></a>

# 3. Unity Guidelines

## 3.1 Unity lifecycle event methods come before other methods

Instead of:

```csharp
public void DoSomething()
{
}

private void Awake()
{
}

private void Start()
{
}
```

Do:

```csharp
private void Awake()
{
}

private void Start()
{
}

public void DoSomething()
{
}
```

## 3.2 Treat warnings as errors and fix them

Warnings pollute the console and make it difficult to develop new features.

## 3.3 Do Not Use GameObject.Find();

## 3.4 Cache Results of GetComponent<>();

## 3.5 Avoid large hierarchies in scenes

Split your hierarchies. If your GameObjects do not need to be nested in a hierarchy, simplify the parenting. Smaller hierarchies benefit from multithreading to refresh the Transforms in your scene. Complex hierarchies incur unnecessary Transform computations and more cost to garbage collection.

## 3.6 ****Transform once, not twice****

When moving Transforms, use [Transform.SetPositionAndRotation](https://docs.unity3d.com/ScriptReference/Transform.SetPositionAndRotation.html?utm_source=demand-gen&utm_medium=pdf&utm_campaign=asset-links-gmg-choose-unity-for-mobile&utm_content=optimize-mobile-game-performance-ebook) to update both position and rotation at once when required. This avoids the overhead of modifying a transform twice.

## 3.7 Only inherit from Monobehavior when necessary

Only use Monobehaviour when:

1. You need to attach to a GameObject 
2. You need to hook into Unity’s lifecycle events
3. You need to receive collision events 
4. You need to receive events from native code
5. You need to run coroutines

## 3.8 If you require a Monobehaviour, encapsulate the functionality in a standard C# class.

If you require a Monobehaviour, encapsulate the functionality in a standard C# class and use that:

```csharp
using UnityEngine;
using UnityEngine.SceneManagement;

namespace PricklyBear.SDK
{
  // ServiceLocatorComp is used just to hook into Unity events. All functionality
  // is handled by the ServiceLocator object
  public class ServiceLocatorComp : MonoBehaviour, IServiceLocator
  {
    public static ServiceLocatorComp Instance { get; private set; }

    // ServiceLocator class contains the required functionality
    private readonly IServiceLocator serviceLocator = new ServiceLocator();

    private void Awake()
    {
      if (Instance != null && Instance != this)
      {
        Destroy(this);
      }
      else
      {
        Instance = this;
      }
    }

    public void AddGlobalService<TGameService>(TGameService serviceInstance)
    {
      serviceLocator.AddGlobalService(serviceInstance);
    }

    public void AddServiceForScene<TGameService>(TGameService serviceInstance)
    {
      serviceLocator.AddServiceForScene(serviceInstance);
    }

    public TGameService Get<TGameService>()
    {
      return serviceLocator.Get<TGameService>();
    }

    private void OnEnable()
    {
      SceneManager.sceneLoaded += OnSceneLoaded;
    }

    private void OnDisable()
    {
      SceneManager.sceneLoaded -= OnSceneLoaded;
    }

    private void OnSceneLoaded(Scene scene, LoadSceneMode mode)
    {
      serviceLocator.OnSceneChange(scene.name);
    }
  }
}
```

They have to be attached to GameObjects making them difficult to share behaviour between classes. If it’s a traditional class, you can just create a new object of that type. 

## 3.9 Avoid Singletons unless they are required in all scenes

Singletons create tightly coupled code, which is hard to change and test. Use the ServiceLocator instead.

## 3.10 Do not use Debug.Log

It's seriously slow as it has to pause execution to build a stack trace for each log. It is also a security concern as anything we log is stored as plaintext on the users device.

Use the IDebugLogger service instead. This will log only in the editor and on development builds. 

Instead of:

```csharp
Debug.Log("I'm a log");
Debug.LogWarning("I'm a warning");
Debug.LogError("I'm an error");
```

Do:

```csharp
DebugPB.Log("I'm a log", DebugLogLevel.Log);
DebugPB.Log("I'm a warning", DebugLogLevel.Warning);
DebugPB.Log("I'm an error", DebugLogLevel.Error);
```

---