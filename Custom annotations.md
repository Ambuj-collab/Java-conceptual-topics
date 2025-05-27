## Annotated methods
To execute code associated with a specific annotated method in Java, reflection is used to locate and invoke the method at runtime. Here's a breakdown of the process:  

- **Define the Annotation**: First, the custom annotation needs to be defined.
  ```
    import java.lang.annotation.ElementType;
    import java.lang.annotation.Retention;
    import java.lang.annotation.RetentionPolicy;
    import java.lang.annotation.Target;
    
    @Retention(RetentionPolicy.RUNTIME)
    @Target(ElementType.METHOD)
    public @interface RunMe {
    }
  ```

- **Annotate Methods**: Apply the custom annotation to the methods intended for execution.
  ```
      public class MyClass {
        @RunMe
        public void doSomething() {
            System.out.println("Executing doSomething");
        }
    
        public void doSomethingElse() {
            System.out.println("Executing doSomethingElse");
        }
    
        @RunMe
        public void doAnotherThing() {
            System.out.println("Executing doAnotherThing");
        }
    }
  ```

- **Find and Invoke Annotated Methods**: Use reflection to find and execute methods marked with the annotation.
  ```
    import java.lang.reflect.Method;
    
    public class Main {
        public static void main(String[] args) {
            MyClass obj = new MyClass();
            Class<?> clazz = obj.getClass();
    
            for (Method method : clazz.getDeclaredMethods()) {
                if (method.isAnnotationPresent(RunMe.class)) {
                    try {
                        method.invoke(obj);
                    } catch (Exception e) {
                        e.printStackTrace();
                    }
                }
            }
        }
    }
  ```

This code retrieves all declared methods of the MyClass, checks for the RunMe annotation, and invokes the annotated methods. The output will be:
  ```
  Executing doSomething
  Executing doAnotherThing
  ```

## Annotated class
Here's how to check if a class is annotated with a specific annotation in Java:
- Get the Class object:
Obtain the Class object representing the class you want to inspect. This can be done using YourClass.class or object.getClass().
- Use isAnnotationPresent():
Call the isAnnotationPresent() method on the Class object, passing the annotation class as an argument. This method returns true if the annotation is present on the class, and false otherwise.
```
Class<?> clazz = MyClass.class; // Get the Class object
boolean isAnnotated = clazz.isAnnotationPresent(MyAnnotation.class); // Check for the annotation

if (isAnnotated) {
    // Class is annotated with @MyAnnotation
    System.out.println("Class is annotated");
} else {
    // Class is not annotated with @MyAnnotation
    System.out.println("Class is not annotated");
}
```

```
import java.lang.annotation.ElementType;
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;
import java.lang.annotation.Target;

// Define a custom annotation
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.TYPE) // can only be applied to classes
@interface MyAnnotation {
    String value() default "";
}

// Example class with the annotation
@MyAnnotation(value = "example")
class MyClass {
}

// Example class without the annotation
class AnotherClass {
}

public class Main {
    public static void main(String[] args) {
        // Check if MyClass is annotated with @MyAnnotation
        Class<?> clazz1 = MyClass.class;
        boolean isAnnotated1 = clazz1.isAnnotationPresent(MyAnnotation.class);
        System.out.println("MyClass is annotated: " + isAnnotated1);

        // Check if AnotherClass is annotated with @MyAnnotation
        Class<?> clazz2 = AnotherClass.class;
        boolean isAnnotated2 = clazz2.isAnnotationPresent(MyAnnotation.class);
        System.out.println("AnotherClass is annotated: " + isAnnotated2);
    }
}

```
