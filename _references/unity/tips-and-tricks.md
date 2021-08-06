---
# BASICS
refid    : rTipsTricks
title    : "Tips & Tricks"
date     : 2015-11-02
subtitle : "Helpful tips and tricks for working in Unity."
author   : aStardog

# IMAGES
bg-img-path  : "001.jpg"
bg-img-scale : 250%
icon-fa-id   : f0d0

# OPTIONS - REFERENCE
isAvailable    : true
type           : unity
rel-tutorials  : 
rel-references : [rTipsTricksCode]
complexity     : 1

# OPTIONS - GENERAL
isPublic : true
---
* TOC
{:toc}

## Snap GameObject to floor/surface/vertex

Select a GameObject with the Move Tool `W`, then hold `V`.

- Snap vertex to vertex - Drag the square over any vertex.
- Snap vertex to vertex (with rounded position numbers) - Drag the square over any vertex while holding `Ctrl`.
- Snap vertex to surface - Drag the square over any surface while holding `Ctrl-Shift`.

## Attributes

Attributes are placed above variables/functions. Here are some useful ones.

### Header

Header allows the inspector to display a title/header above variables.

{% highlight csharp %}
[Header("Info")]
public string _name;
public string _description;

[Header("Settings")]
public int _width;
public int _height;
{% endhighlight %}

### TextArea



### Multiline



### HideInInspector

Serializes a field, but will not show it in the inspector.

{% highlight csharp %}
[HideInInspector]
private int _varName;
{% endhighlight %}

### Range

{% highlight csharp %}
[Range(0, 100)]
public int _limitedRange;
{% endhighlight %}

### SerializeField

Allows private fields to show in the inspector.

### ContextMenu

ContextMenu allows you to run a function by right-clicking on a Component in the inspector.

{% highlight csharp %}
[ContextMenu("Name")]
void FunctionName()
{
	...
}
{% endhighlight %}

### ContextMenuItem

ContextMenuItem allows you to run a function by right-clicking on a variable/field in the inspector.

{% highlight csharp %}
[ContextMenuItem("Reset", "ResetBiography")]
public string playerBiography = "";

void ResetBiography()
{
	playerBiography = "";
}
{% endhighlight %}

### MenuItem

<a href="https://docs.unity3d.com/ScriptReference/MenuItem.html" class="external">MenuItem</a> allows you to run a function from an editor dropdown menu or hotkey.

{% highlight csharp %}
[MenuItem ("MyMenu/Do Something")]
static void DoSomething()
{
	...
}
{% endhighlight %}

### CreateAssetMenu

Creates a <a class="external" href="https://unity3d.com/learn/tutorials/modules/beginner/live-training-archive/scriptable-objects">ScriptableObject</a> asset on disk. It can store data and be used like a profile.

{% highlight csharp %}
[CreateAssetMenu(fileName = "GraphicsSetting", menuName = "MyGame/Graphics Setting", order = 1)]
public class GraphicsSettingsData : ScriptableObject {

	[Header("Info")]
	public string _name;
	public string _description;
	
	[Header("Settings")]
	public bool _bloomEnabled;
	public bool _ambientOcclusionEnabled;
	public bool _antialiasingEnabled;

}
{% endhighlight %}

### SelectionBase

Allows you to select this GameObject in the scene instead of a child.

{% highlight csharp %}
[SelectionBase]
public class Script : MonoBehaviour { }
{% endhighlight %}

### Attribute Extensions

- [NaughtyAttributes](https://github.com/dbrizov/NaughtyAttributes)

## Logs

Here are some cool things you can do with <a href="https://docs.unity3d.com/ScriptReference/Debug.Log.html" class="external">Debug.Log</a>.

### Single-line console log entries

You can reduce the size of console (Window > General > Console) entries by clicking the 3 dots in the top-right and choosing Log Entry > 1 line.

### Formatting

Use <a href="https://docs.unity3d.com/Manual/StyledText.html" class="external">Rich Text</a> for formatting.

{% highlight csharp %}
Debug.Log("<b><color=red>Red and Bold!</color></b>");
{% endhighlight %}

### Line break / New Line

Use `\n` to create a new line.

{% highlight csharp %}
Debug.Log("First Line\nSecond Line");
{% endhighlight %}

### Highlight GameObject in hierarchy

When selecting a log entry, you can highlight the GameObject it came from.

{% highlight csharp %}
Debug.Log("Hello World!", gameObject);
{% endhighlight %}

## Shortcut to add/subtract or increment/decrement

{% highlight csharp %}
public int number = 10;

// Full (adds one to variable)
number = number + 1;

// Shortened
number += 1;

// Shortest
number++;
{% endhighlight %}

## Save / Load object selection in hierarchy and project view

Ctrl + Alt + (Number) = Save selection
Ctrl + Shift + (Number) = Load selection

It works with GameObjects and Assets, including mixing the two.

## Save content from play mode in edit mode

- Play your game, make changes.
- Right-click and Copy the gameobject(s) you want to save.
- Stop playing, right-click in hierarchy and Paste.

The same also works for modified components.

## Hierarchy - Expand/Collapse All

- Hold left-alt when clicking an arrow to expand/collapse all of the children of a GameObject.

## Inspector - Expressions

Number fields support math expressions. Typing 1+1 then enter will output 2.

Function support - sqrt, sin, cos, tan, floor, ceil, round.

Distribution over multi-selection (L, R) and can refer to current value to change it across multi-selection (+=3, *=2).

<a href="https://twitter.com/aras_p/status/1372446086078590978" class="external">Developer Tweet</a>

## Inspector - Show auto-properties

You can now use `[field: SerializeField]` to show <a href="https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties" class="external">auto-implemented properties</a> in Unity's inspector.

{% highlight csharp %}
[SerializeField] // Show private field in inspector.
private int number;

[field: SerializeField] // Show property in inspector.
public string MyProperty { get; set; }
{% endhighlight %}
