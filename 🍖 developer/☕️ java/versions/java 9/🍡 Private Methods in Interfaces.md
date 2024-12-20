
[[🧁 Java9]] [[🧃 Interface]]

В Java 8 мы можем предоставлять реализацию методов в интерфейсах с помощью методов по умолчанию и статических методов. Однако мы не можем создавать частные методы в интерфейсах. Чтобы избежать избыточного кода и обеспечить большую возможность повторного использования, Oracle Corp. представила частные методы в интерфейсах Java SE 9. Начиная с Java SE 9, мы также можем писать частные и частные статические методы в интерфейсе с помощью ключевого слова 'private'.

```java
public interface Card{  
     private Long createCardID(){  
      // Method implementation goes here.  
     }  
  
    private static void displayCardDetails(){  
      // Method implementation goes here.  
    }  
    
}
```