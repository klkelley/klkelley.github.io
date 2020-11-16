---
layout: post
comments: true
title: Decorator Pattern  
date: 2018-05-07 11:01:00
description: Decorator pattern explained 
---


The decorator pattern's intent can be described as: 
> A structural design pattern that lets you attach new behaviors to objects
by placing them inside wrapper objects that contain these behaviors. 

You can also think of it as wrapping a gift, putting it in a box, and then
wrapping that box. 

When might you want to use the decorator pattern? Consider the scenario that 
you have to add or remove responsibilities from an object dynamically, 
but you need to do it in a way to that it stays compatible with the rest of the
application's code. 

You may think that inheritance could be a good approach to extend behavior of an object
but we can't use inheritance to add or remove behavior at runtime with inheritance. This 
is where the decorator pattern comes into play. 


Typically, there are four components to the decorator pattern: 

* Component - The component is the interface for objects that can have responsibilities added to them dynamically. 
* Concrete Component - Defines an objects to which additional responsibilities can be added
* Decorator - Maintains a reference to a Component object and defines an interface that conforms to the Component's interface. 
* Concrete Decorators - Extend the functionality of the component by adding behavior. 


Here is a UML diagram illustrating the pattern with the different components

![uml-decorator](http://best-practice-software-engineering.ifs.tuwien.ac.at/patterns/images/decorator_simple.jpg)



Now that we have some base knowledge on the intent and the different participants that make up the decorator pattern let's check out an example. 


Consider that we want to implement different types of cars. We could implement a `Car` interface
and create a `StandardCar` and have other types of cars like `LuxuryCars` and `SportsCar` extend 
`StandardCar` but what if we wanted to have a car that had features of both types of cars at runtime. This wouldn't be quite possible and if we stick with this inheritance model the amount of subclasses for all the different types of cars and their features would be immense. 

Instead, we can use the decorator pattern to solve this problem. 


Our **component** can be either and interface or abstract class but we'll stick with an interface for this example. 


```java 

public interface Car {
  void makeCar();
}

```



The **concrete component** would then look something like this: 


```java 

public class StandardCar implements Car {

  @Override
  public void makeCar() {
    System.out.println("Standard Car.");
  }
}

```


The **decorator** would be modeled as follows: 


```java 

public class CarDecorator implements Car {
  private Car car;

  public CarDecorator(Car car) {
    this.car = car;
  }

  @Override
  public void makeCar() {
    this.car.makeCar();
  }
}

```



Now we're ready for our **concrete decorators** like `LuxuryCar` and `SportsCar`


```java 

public class SportsCar extends CarDecorator {

  public SportsCar(Car car) {
    super(car);
  }

  @Override
  public void makeCar() {
    super.makeCar();
    System.out.println("Adding cool sports car features");
  }
}


public class LuxuryCar extends CarDecorator {

  public LuxuryCar extends CarDecorator(Car car) {
    super(car);
  }

  @Override
  public void makeCar() {
    super.makeCar();
    System.out.println("Adding fancy luxury car features");
  }
}

```



Now we can create all types of cars. 



```java

public class Main {

  public static void main(String[] args) {
    Car sportsCar = new SportsCar(new StandardCar());
    sportsCar.makeCar();

    Car sportsLuxuryCar = new SportsCar(new LuxuryCar(new StandardCar()));
    sportsLuxuryCar.makeCar();
  }
}


// => Standard Car. Adding cool sports car features.
// => Standard Car. Adding fancy luxury car features. Adding cool sports car features. 

```



So, in summary, this pattern is really helpful when you need to provide runtime modifications. It's also much easier to maintain vs having an unlimited number of subclasses. I also liked this analogy if you're familiar with the strategy pattern:  
> Decorator lets you change the skin of an objects. Strategy lets you change the guts. Lastly, if you want to see a non-contrived example implementing the decorator pattern, check out the `HandlerWrapper` class in the `Jetty.server` library. 


