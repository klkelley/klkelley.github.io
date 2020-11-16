---
layout: post
comments: true
title: Java Classpath
date: 2018-03-20 16:10:00
description: What in the world is a Classpath?
---


As a developer who is new to Java, I think understanding the classpath has been 
rather confusing. The official docs don't do a great job at explaining what it is 
and many blog posts out there talk about _how_ to set the classpath and not about
the _why_. 

I always understand things better when I can comprehend the _why_ so let's
dig into what a classpath really is. 

In order to understand the classpath we'll first discuss some other topics like packages 
and imports as well as it's important to talk about before we get into the actual classpath. 

### Imports
<br>

Imports are imported using their fully qualified class names (FQCN). For example, if we wanted to import and use a HashMap we could say: `import java.util.HashMap;`. Doing so makes the HashMap class
available without having to fully qualify it every time it appears in the source code. 

So, while programming in Java we often use import statements like this and the one mentioned above: 



```java
import org.company.SampleClass;
```



I have all kinds of import statements in my current project  but thanks to IntelliJ, I've never really had to think about it. So what does the import statement mean? It makes the `SampleClass` available in the package `org.Company` available to our current class. 
So when we call `SampleClass sampleClass = new SampleClass();` the JVM knows where to find the `SampleClass` (more on this later). 


### Packages
<br>

A package is a collection of Java entities like classes, interfaces, exceptions, and errors. They are used for a few different reasons: 

1. Resolving name conflicts of classes by prefixing
the class with a package name for example `me.karakelley.somePackage.Circle` and `me.karakelley.otherPackage.Circle`. They have the same class name but since they belong to different packages they are two distinct classes. You'll notice that I also used my domain name which I'll touch on in a bit. 

2. Access Control. Aside from `public` and `private`, Java has two access control modifiers, `protected` and default that are related to a package. A protected entity is only accessibly by classes in the same package and its subclasses. An entity without an access control modifier (i.e. default) is accessible by classes in the same package only.  

3. For distributing a collection of reusable classes, usually in the format of a JAR. 


I brought to light the fact that I was using my domain name in the examples. This is because per naming conventions, a package name is made up of the reverse of your Internet domain name to ensure uniqueness. 

The last thing to note about packages is that the package structure reflects where on the disk your code lives. In other words, the package is closely associated with the directory structure used to store the classes.

For example say we have a source file name `Plant.java` with a package statement of `me.karakelley.something` then the path structure
would look something like this: 

```
$BASE_DIR/me/karakelley/something/Plant.java
``` 


Note: `$BASE_DIR` denotes the base directory of the package and could be located **anywhere** in the file system. Which is what brings us (finally) to the classpath. 


### Classpath 
<br> 

So as I just mentioned our base directory of our packages can be located anywhere in the file system. It doesn't make much sense to have the JVM look
through every folder on your machine so you need to 
provide it with a list of places to look. 
You do this by putting the folder and jar files on your classpath. 

More formally speaking however it's defined as: 
> Classpath is a parameter in the JVM or the Java compiler that specifies the 
location of user-defined classes and packages. The parameter may be set either
on the command-line or through an environment variable.

There are a few different ways to set the classpath. 
The most simple way is to use the `CLASSPATH` environment variable however the `-classpath` version is preferred because it allows you to set the classpath individually for each application without affecting other applications. You can use the `-classpath` like so when you run 
your application. 

```
$ javac -classpath path/to/jar/file MyMainClass.java
```

Alternatively, if your program is enclosed in a JAR file you can add the JAR file to the 
classpath within a manifest file. Doing so in this manner lets you run your program like so: 


```
java -jar path/to/myJarFile.jar [optional args]
```

Using build tools like Maven and Gradle also make this process a bit easier I think. 


I feel as though "classpath" isn't a very intuitive word so just remember that the classpath serves as a way to point the JVM in the right direction when it starts 
looking for your classes and packages. 


So it turns out the classpath isn't all that special or as intimidating as I thought
but it's important to understand when developing Java applications. 

