[[🧁 Java9]]

added in 9 java
### Когда это полезно?
`StackWalker` полезен при отладке, написании библиотек или инструментов, которые должны анализировать или логировать стек вызовов. Он также может быть полезен в ситуациях, где вам нужно получить информацию о том, кто вызвал тот или иной метод, но вы хотите это делать эффективно и гибко.
```
public class StackWalkerExample { 
	public static void main(String[] args) { 
	exampleMethod();
} 
public static void exampleMethod() { 
	StackWalker walker = StackWalker.getInstance(); 
	walker.forEach(frame -> { System.out.println(frame.getClassName() + " " +  frame.getMethodName());
}); 
} 
}
```

В этом примере `StackWalker` перебирает все фреймы стека вызовов и выводит на экран имя класса и имя метода для каждого фрейма.