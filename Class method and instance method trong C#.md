---
title: "Class method của Ruby trong C#"
tags: 'C#,'
date: '2018-06-19'

---

<p>Vì đọc <a href="1">bài này</a> nên tự nhiên nghĩ đến static method (class method) &amp; normal method (instance method) trong C#. Vậy nên viết cái này<br>
Không giống Ruby, trong C# thì class method và instance method không đa hình, nghĩa là nếu viết như này:</p>
<pre class=" language-cs"><code class="prism  language-cs">    public class Animal
    {
        public static void Hello()
        {
        }
        public void Hello()
        {
        }
    }
</code></pre>
<p>Các bạn sẽ bị lỗi:</p>
<blockquote>
<p><code>CS0111</code>	Type ‘Animal’ already defines a member called ‘Hello’ with the same parameter types</p>
</blockquote>
<p>Còn khi gọi, thì cũng giống Ruby, static method không thể được gọi từ 1 <code>instance</code> mà phải gọi từ class</p>
<pre class=" language-cs"><code class="prism  language-cs">class Program
    {
        static void Main(string[] args)
        {
            Animal a = new Animal();
            Animal.Hello();
            a.Hello();  //Error: CS0176	
            a.HelloHuman();
        }
    }
</code></pre>
<blockquote>
<p><code>CS0176</code> Member ‘Animal.Hello()’ cannot be accessed with an instance reference; qualify it with a type name instead</p>
</blockquote>
<blockquote>
<p>Written with <a href="https://stackedit.io/">StackEdit</a>.</p>
</blockquote>

