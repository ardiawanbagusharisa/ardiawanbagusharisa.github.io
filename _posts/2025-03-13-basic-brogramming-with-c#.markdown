---
layout: post
title: "Basic Programming with C#"
date: 2025-06-14 06:39:50 +0800
categories: Programming 
tags: Programming C#
---

Originally, I wanted to write the basic programming tutorial using C# as the language by my own. But, then I realised that there are already good tutorials. Youy can follow the following references, even the microsoft's course also provide free certification. Maybe I will also write my own tutorial in times. 

References: 
1. Microsoft learn (free certificate): [link](https://learn.microsoft.com/en-us/collections/yz26f8y64n7k07) or [link](https://learn.microsoft.com/en-us/training/paths/get-started-c-sharp-part-6/). 
2. More complete resource from Microsoft: [link](https://learn.microsoft.com/en-us/dotnet/csharp/tour-of-csharp/) or [link](https://dotnet.microsoft.com/en-us/learn/csharp). 
3. Programmiz: [link](https://www.programiz.com/csharp-programming). Programmiz provides great tutorials, although, too many ads. So, yeah I will probably provide one which does not show any ads. 

So, why `c#`?  
From my personal experience, `c#` is way safer programming language compare to `c` and `c++` because it has garbage collector that help us to handle the memory allocation. I think it is also keeping the programming logic paradigm compare to some modern languages like `python`. 

What can we use `c#` for? *not limited to.  
- Web Development (with ASP.NET Core)
- Game Development (with Unity)
- Desktop Applications (with .NET MAUI, WPF, Windows Forms)
- Cloud and AI Services (with Azure)

*It works best in Visual Studio Community or VS Code. 

<br>

---

# C# Example
Here are some examples of C# syntax: 
### 1. Variables  
Imagine you need to store pieces of information, like a number, a name, or whether something is true or false. That's what variables are for! They're named storage locations in your computer's memory.  

```cs
int age = 30; // Stores a whole number (integer)
string name = "Alice"; // Stores text (string)
bool isActive = true; // Stores true or false (boolean)
```

### 2. Data Types
Each variable has a data type that tells the computer what kind of information it will hold. `int`, `string`, and `bool` in the example above are just a few common data types. 

### 3. Operators
Operators let you perform actions on your data.
- Arithmetic: `+` (add), `-` (subtract), `*` (multiply), `/` (divide)
- Comparison: `==` (equals), `>` (greater than), `<` (less than)
- Logical: `&&` (AND), `||` (OR)

```cs
int sum = 5 + 3; // sum will be 8
bool isAdult = age > 18; // isAdult will be true if age is 30
```

### 4. Conditional Statements
Computers can make decisions based on conditions! if statements allow your program to execute different blocks of code depending on whether a condition is true or false. Here, `Console.WriteLine()` is a built function from .NET framework to help us displaying texts in our console. 

```cs
if (age >= 18)
{
    Console.WriteLine("You are an adult!");
}
else
{
    Console.WriteLine("You are a minor.");
}
```

### 5. Loops
Sometimes you need to repeat a set of instructions multiple times. Loops are perfect for this! `for` and `while` loops are very common. 
```cs
for (int i = 0; i < 5; i++)
{
    Console.WriteLine("Hello, C#!"); // This will print 5 times
}
```

--- 

Check out another [Post][post] for more. 

[post]: https://ardiawanbagusharisa.github.io/blog

<p><strong>Categories:</strong> 
  {% for category in page.categories %}
    <a href="/category/{{ category | slugify }}/">{{ category }}</a>{% unless forloop.last %}, {% endunless %}
  {% endfor %}
</p>

<p><strong>Tags:</strong> 
  {% for tag in page.tags %}
    <a href="/tag/{{ tag | slugify }}/">{{ tag }}</a>{% unless forloop.last %}, {% endunless %}
  {% endfor %}
</p>