---
layout: post
title:  "C# params keyword"
date:   2016-06-28 19:35:00 +0800
categories: .net c# 
---
The params keyword allows you to define a method that takes a variable number of arguments as parameters. The params parameter is declared as an array, and each argument passed to the method can be accessed as with any regular array. The params keyword must be declared last in the method signature. For example:

{% highlight csharp %}
public static MethodOne(params string[] args)
{
     //code, such as args[1] to access the second element...
}
{% endhighlight %}

Can be called with

```
MethodOne(1,2,3)
```

or

```
MethodOne(1,2,3,4,5)
```

or even

```
MethodOne()
```

This looks very similar to the main method in the default console application:

{% highlight csharp %}
static void Main( string[] args)
{
}
{% endhighlight %}

which also allows passing a variable number of arguments to the method - what's the difference? Basically just how you call the method - the Main method requires an array to be instantiated:

```
Main(new string[]{"one","hello"});
```

whereas using the params keyword doesn't need the array to be instantiated. In action:

{% highlight csharp %}
class Program
{
    static void Main( string[] args)
    {
    }

    static void Main2( params string[] args)
    {

    }

    static void CallIt()
    {
        Main( new string[] { "one", "two" });
        Main2( "one", "two" );
    }
}
{% endhighlight %}

Opening up Ildasm.exe on this shows that Main and Main2 both have the signature (string[]), and the CallIt method compiles into:

```
.method private hidebysig static void  CallIt() cil managed
{
  // Code size       58 (0x3a)
  .maxstack  8
  IL_0000:  nop
  IL_0001:  ldc.i4.2  
  IL_0002:  newarr     [mscorlib]System.String
  IL_0007:  dup
  IL_0008:  ldc.i4.0
  IL_0009:  ldstr      "one"
  IL_000e:  stelem.ref
  IL_000f:  dup
  IL_0010:  ldc.i4.1
  IL_0011:  ldstr      "two"
  IL_0016:  stelem.ref
  IL_0017:  call       void ConsoleApplication1.Program::Main(string[])
  IL_001c:  nop
  IL_001d:  ldc.i4.2
  IL_001e:  newarr     [mscorlib]System.String
  IL_0023:  dup
  IL_0024:  ldc.i4.0
  IL_0025:  ldstr      "one"
  IL_002a:  stelem.ref
  IL_002b:  dup
  IL_002c:  ldc.i4.1
  IL_002d:  ldstr      "two"
  IL_0032:  stelem.ref
  IL_0033:  call       void ConsoleApplication1.Program::Main2(string[])
  IL_0038:  nop
  IL_0039:  ret
} // end of method Program::CallIt
```

As you can see, the compiler is generating the string array for both method calls here. So it's just syntactic sugar, but could be useful for reducing the effort to call particular methods.

Further reading:
An interesting corner case about how the applicable function can become overloaded using Object type parameters: <https://blogs.msdn.microsoft.com/oldnewthing/20130806-00/?p=3603>
