# Important

- compiled
- strongly, statically typed (declare type of every variable, and it can't change)
- is run in a *Java Virtual Machine* (JVM) which allows platform independence
- everything goes in a class
- if you declare a variable without initializing it, it gets initialized to 0 or equivalent

## getting started

- Download JDK from [Oracle](https://www.oracle.com/java/technologies/downloads/)
- try to run the **javac** command in powershell
  - if not recognized, you must add the *jdkxxxx/bin* folder to your PATH
- create a file called **ClassName.java**
- put some code in a class with the same name as the file (*main()* is entry point of the program)
```
public class ClassName {
    public static void main(String[] args){
        System.out.println("Hello World!");
    }
}
```
- in powershell run `javac ClassName.java` which will compile to **ClassName.class** if there are no errors
- in powershell run `java ClassName` to run the code

# data types

## primitives

there's a few more but here's the common ones
- **boolean** holds *true* or *false*
- **char** holds a single character
- **int** is a 32-bit integer
- **long** is a 64-bit integer
- **float** is a low-precision float
- **double** is a high-precision float

## wrapper classes (object types)

wrapper classes put primitives in an object so that we can call methods from them
- **Boolean**
- **Character**
- **Integer**
- **Long**
- **Float**
- **Double**

## other built-in object types

**String** is a sequence of characters
**BigInteger** is an integer that can be as big as you want

# control flow an stuff

## if, else if, else and conditions

same syntax as C++ and JavaScript
```
if (score >= 90)
    System.out.println("Amazing!");
else if (score >= 80)
    System.out.println("Great!");
else
    System.out.println("You can do better!");
```

comparison operators and logical operators used in conditions
- == != > < >= <=
- ! || &&

ternary operator
```
System.out.println(size > 10 ? "You have big feet." : "Nice shoes.");
```

## switch statement

same syntax as C++
```
switch(day){
    case 1:
        System.out.println("Ugh another week");
        break;
    case 2:
    case 3:
    case 4:
        System.out.println("I can't wait for this week to be over");
        break;
    default:
        System.out.println("I love the weekend");
}
```
