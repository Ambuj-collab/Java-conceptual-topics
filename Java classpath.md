### Understanding Java’s Classpath:
The classpath is an environment variable used by the Java Virtual Machine (JVM) to locate and load classes when running a Java program. It specifies a list of directories, JAR files, and ZIP files where the JVM should look to find and load class files.
We can set the classpath from the command line or in an integrated development environment (IDE).

#### Setting the Classpath via the Command Line
To set the classpath via the command line, we use the **-classpath** option when running the **java** command:
```console
java -classpath /path/to/class/files MyProgram
```
Here, MyProgram is the name of the main class, and /path/to/class/files is the directory where the class file is located. If we have multiple directories and/or JAR files, we can separate them using a colon:
```console
java -classpath /path/to/classes:/path/to/lib.jar MyProgram
```
dot (.) is the default value of CLASSPATH.
#### References:  
  1) https://www.baeldung.com/java-classpath-vs-build-path#:~:text=The%20classpath%20is%20an%20environment,find%20and%20load%20class%20files.
  2) https://dev.to/martingaston/understanding-the-java-classpath-building-a-project-manually-3c3l
  3) https://en.wikipedia.org/wiki/Classpath

### Understanding Java's Build Path:
The build path is a list of all the resources that are required to build a Java project, including source files, class files, libraries, and other dependencies. The Java development environment such as Eclipse, IntelliJ IDEA, or NetBeans uses the build path to compile and build the Java project.
The build path can be set in the project directories of both Eclipse and IntelliJ IDEA. 
#### References:  
  1) [https://www.baeldung.com/java-classpath-vs-build-path#:~:text=The%20classpath%20is%20an%20environment,find%20and%20load%20class%20files.](https://www.baeldung.com/java-classpath-vs-build-path#build-path)
