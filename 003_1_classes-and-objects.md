# Classes and Objects

A `Class` is a blueprint for creating objects. It defines the state and behavior of the objects that will be created.

An `object` is an instance of a Class.


Example of JAVA `Class`

**src/Person.java**

```java
public class Person {

    private String name;
    private int age;

    public Person(String name, int age){
        // inside the constructor we use this to tell JAVA we are referring to the object and not the class
        this.name = name;
        this.age = age;
    }

    public String getName(){
        return name;
    }

    public int getAge(){
        return age;
    }
}
```

**src/Test.java**

```java
public class Test {
    public static void main(String args[]) {
        Person peter = new Person("Peter", 30);
        System.out.println(peter);
        // Person@36baf30c
    }
}
```

By default, when we print an object like `System.out.println(peter);`, JAVA will log CLASS @ OBJECT_HASHCODE.

If we want to log a user-friendly output of the object we need to override the toString() method of the class.

```java
@Override
public String toString() {
    return "Name: " + name + " age: " + age;
}
```

Example:

```java
public class Person {

    private String name;
    private int age;

    public Person(String name, int age){
        // inside the constructor we use this to tell JAVA we are referring to the object and not the class
        this.name = name;
        this.age = age;
    }

    public String getName(){
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge(){
        return age;
    }

    @Override
    public String toString() {
        return "Name: " + name + " age: " + age;
    }
}
```

Result: `Name: Peter age: 30`

---

In relation to `memory` we have

1. Heap: where objects are stored
2. Stack: where primitives are stored and variables that references to objects

Remember...
* Reference types store a reference to the location of the object in memory (heap)
* Primitive types store the value in the stack

```java
public class Test {
    public static void main(String args[]) {

        Person peter = new Person("Peter", 30); // Name: Peter age: 30
        Person paul = peter; // Name: Peter age: 30
        paul.setName("Paul"); // Name: Paul age: 30
        System.out.println(peter); // // Name: Paul age: 30
    }
}
```