# Important

- compiled
- strongly, statically typed (declare type of every variable, and it can't change)
- is run in a *Java Virtual Machine* (JVM) which allows platform independence
- everything goes in a class
- if you declare a variable without initializing it, it gets initialized to 0 or equivalent

## getting started

- Download JDK from [Oracle](https://www.oracle.com/java/technologies/downloads/)
- try to run the **javac** command in powershell
  - if not recognized, you must add the *Program Files/Java/jdk1.8.0_341/bin* folder to your PATH (in settings search for *Advanced System Settings*, click *Environment Variables*, edit *Path*, *New*, *Browse* to the location)
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
- **char** holds a single character, must use 'a' single quotes
- **int** is a 32-bit integer, can put underscores between digits to be easier to read
- **long** is a 64-bit integer
- **float** is a 32-bit float, use 2.4*f* when writing literals because 2.4 is a double
- **double** is a 64-bit float (higher precision)

the smaller ones will implicitly typecast to the larger ones, otherwise error  
explicit typecast larger to smaller like in C++
```
long l = 12932958;
int i = (int) l;
```

## wrapper classes (object types)

wrapper classes put primitives in an object so that we can call methods from them
- **Boolean**
- **Character**
- **Integer**
- **Long**
- **Float**
- **Double**

## other built-in object types

- **String** is a sequence of characters, immutable
  - comparing Strings with == compares objects, use `str1.equals(str2)` instead
  - `str1.length()` for the length
  - `str1.toUpperCase()` and `str1.toLowerCase()`
  - format with `String formatted = String.format("%s owes me %.2f dollars","John",5);`
  - remove starting and ending whitespace with `str1.trim()`
  - must use double quotes (single quotes are for char)
  - to search for first index of substring str2 in str1 `str1.indexOf(str2)` (returns -1 if not found)
- **BigInteger** is an integer that can be as big as you want

## arrays vs ArrayLists

a fixed-length array can be made like this, which fills it with default values
```
int [] coolArray = new int[15];
```
or like this to hardcode starting values
```
int[] coolArray = {1,2,3,4,5,6,7,8,7,6,5,4,3,2,1};
```
- typical `coolArray[i]` syntax to get and set values at index *i*
- `coolArray.length` to get the length
- manually loop through the array to print it in a meaningful way
  - or `import java.util.Arrays` and use `Arrays.toString(coolArray)`

`ArrayList<T>` is a generic object-based adjustable array
- it can't hold primitive types
- can hold different types via parent class, `ArrayList<Object>` for all
- does not use bracket syntax

```
ArrayList<Integer> coolerArray = new ArrayList<Integer>();
coolerArray.add(100); //puts the new value at the end of the array (implicit cast to Integer)
System.out.println(coolerArray.get(0)); //reads the value at index 0
System.out.println(coolerArray.size()); //the length of the array
coolerArray.set(0,50); //puts new value 50 at index 0
coolerArray.remove(0); //removes the element at index 0
coolerArray.clear(); //clear the array
System.out.println(coolerArray.isEmpty()); //is the array empty?
```

## HashMap

map keys to values like a dictionary in Python
```
HashMap<String,String> myMap = new HashMap<String,String>();
myMap.put("Bob Barley","Canada");
System.out.println(myMap.get("Bob Barley"));
```

iterate by getting the Set of keys and enhanced for loop
```
Set<String> keys = myMap.keySet();
for(String key : keys)
    System.out.println(key + " => " + myMap.get(key));
```

other HashMap methods
- `.clear()`
- `.containsKey(Object key)`
- `.isEmpty()`
- `.size()`
- `.remove(Object key)`

# control flow and stuff

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

## loops

C++ style while loop and for loop

*enhanced for loop* (basically a for-each/for-in loop)
```
for(Integer i : myArrayList)
{
    System.out.println(i);
}
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

## methods

pretty much the same as C++
```
public class Conversions {
    public double feetInchesToCentimeters(double feet, double inches){
        //code which returns a double
    }
}
```

can overload methods by giving different parameter types/quantity

## constructors

constructors are like methods but there is no return type or return statement
```
public class Test {
    private String name;
    private int score;

    public Test(String name, int score) {
        this.name = name;
        this.score = score;
    }
}
```

## make it modular

- we want to reuse a class? then don't put the main() method in it
- create a separate class with the main method (the *driver* class) which uses the reusable class

import a library class
```
import java.util.Date;
```

then in a method you can create a Date
```
Date date = new Date();
```

dependency injection of your own Sausage class: just use the class in the other class (same directory)
```
public class TestSausage {
    public static void main(String[] args){
        Sausage mySausage = new Sausage();
        System.out.println(mySausage);
    }
}
```

compiling the driver class will also compile its dependencies

## exceptions

make an exception class with the class that throws it
```
class MyException extends Exception{}
class ExceptionThrower{
    public void couldFail() throws MyException{
        //should probably do something
        throw new MyException();
    }
}
```

try/catch in the class that wants to use that method
```
class MainClass {
    ExceptionThrower et = new ExceptionThrower();
    public static void main(String[] args){
        try{
            et.couldFail();
            System.out.println("success");
        }
        catch (MyException e){
            System.out.println("failed");
        }
    }
}
```
