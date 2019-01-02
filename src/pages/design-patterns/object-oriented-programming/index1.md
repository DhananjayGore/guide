# Singleton Design Pattern

**Singleton** is a part of **Gang of Four design pattern** and it is categorized under creational design patterns. In this article, we are going to take a deeper look into the usage of the *Singleton pattern*. It is one of the most simple design pattern in terms of the modelling but on the other hand this is one of the most controversial pattern in terms of complexity of usage.

##### **Definition:** 
The singleton pattern is a design pattern that restricts the instantiation of a class to one object.Let’s see various design options for implementing such a class. If you have a good handle on static class variables and access modifiers this should not be a difficult task. 

##### **Classical Approach**
 Classical Java implementation of singleton  design pattern 
```
class Singleton 
{ 
    private static Singleton obj; 
    // private constructor to force use of 
    // getInstance() to create Singleton object 
    private Singleton() {} 
  `
    public static Singleton getInstance() 
    { 
        if (obj==null) 
            obj = new Singleton(); 
        return obj; 
    } 
} 
`````

##### **Lazy Creation Thread safe**
 
We can make the above non-thread safe implementation thread safe by using synchronization. 
```
 public class Singleton {
    private Singleton inst = null;
    
    private Singleton(){}
    
    public static Singleton getInstance() {
        synchronized(Singleton.class) {
            if(inst == null) {
                inst = new Singleton();
            }
        }
        return inst;
    }
}
`````  

##### **Early Creation Thread safe**
 
There is another approach to make the singleton thread safe by initializing he instance during loading of class. This is achieved by making the member variable as static and initializing it at declaration time. The sample code is shown below:
```
public class Singleton {
    private static Singleton inst = new Singleton();
    
    private Singleton(){}
    
    public static Singleton getInstance() {
        return inst;
    }
}
```
  
**source**
[Wikipedia](http://en.wikipedia.org/wiki/Singleton_pattern)
[OODesign Singleton Pattern](http://www.oodesign.com/singleton-pattern.html)
 
  
