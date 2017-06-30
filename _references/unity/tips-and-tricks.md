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

# OPTIONS - REFERENCE
isAvailable    : true
type           : unity
rel-tutorials  : 
rel-references : 

# OPTIONS - GENERAL
isPublic : true
---
...

* TOC
{:toc}

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



### Range



### SerializeField



### ContextMenu

ContextMenu allows you to run a function by right-clicking on a Component.

{% highlight csharp %}
[ContextMenu("Name")]
void FunctionName()
{
	...
}
{% endhighlight %}

### ContextMenuItem

ContextMenuItem allows you to run a function by right-clicking on a variable/field.

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

## Logs

Here are some cool things you can do with <a href="https://docs.unity3d.com/ScriptReference/Debug.Log.html" class="external">Debug.Log</a>.

### Formatting

Use <a href="https://docs.unity3d.com/Manual/StyledText.html" class="external">Rich Text</a> for formatting.

{% highlight csharp %}
Debug.Log("<b><color=red>Red and Bold!</color></b>");
{% endhighlight %}

### New lines

Logs can look messy, so you can get rid of the line below by using <code>\n</code>.

{% highlight csharp %}
Debug.Log("Cleaner log\n");
{% endhighlight %}

### Highlight GameObject in hierarchy

When selecting a log entry, you can highlight the GameObject it came from.

{% highlight csharp %}
Debug.Log("Hello World!", gameObject);
{% endhighlight %}

