---
title: Class method của Ruby trong C#
date: 2018-06-19 00:00:00 Z
tags: C#,
---

Vì đọc  [bài này](http://localhost:4000/1)  nên tự nhiên nghĩ đến static method (class method) & normal method (instance method) trong C#. Vậy nên viết cái này  
  
Không giống Ruby, trong C# thì class method và instance method không đa hình, nghĩa là nếu viết như này:

```cs
    public class Animal    
	{        
		public static void Hello()        
		{        }        
		public void Hello()        
		{        }    
	}
```
Các bạn sẽ bị lỗi:

> `CS0111`  Type ‘Animal’ already defines a member called ‘Hello’ with the same parameter types

Còn khi gọi, thì cũng giống Ruby, static method không thể được gọi từ 1  `instance`  mà phải gọi từ class

```cs
class Program    
{        
    static void Main(string[] args)        
    {           
		Animal a = new Animal();
		Animal.Hello();            
		a.Hello();  //Error: CS0176            
		a.HelloHuman();        
	}    
}
```

> `CS0176`  Member ‘Animal.Hello()’ cannot be accessed with an instance reference; qualify it with a type name instead

> Written with [StackEdit](https://stackedit.io/).
