# JWNL' (JWNL-prime)

[![Build Status](https://semaphoreci.com/api/v1/projects/99376d44-f586-4054-9300-d38c9a780a9e/594274/badge.svg)](https://semaphoreci.com/danyaljj/jwnl-prime)

This is the refactored version of [JWNL](http://sourceforge.net/projects/jwordnet/) (from version jwnl14-rc2).

- [Documentaion on the property file](doc/propertyFileConfiguration.md). 
- [Documention on `DictionaryToDatabase`](doc/DictionaryToDatabase.md). 

The major reason for this refactoring was to make JWNL (and WordNet) a self-contained maven dependency, without 
the need to define configuration or the need to download the WN. 

Now you can just add it as a maven dependency: 
```xml 
<repositories>
     <repository>
         <id>CogcompSoftware</id>
         <name>CogcompSoftware</name>
         <url>http://cogcomp.org/m2repo/</url>
     </repository>
</repositories>
<dependencies>
    <dependency>
     <groupId>edu.illinois.cs.cogcomp</groupId>
     <artifactId>jwnl-prime</artifactId>
     <version>1.0.3</version>
    </dependency>
 </dependencies>
```
And start loading the application (without the need to download WordNet or add any config files): 

```java 
JWNL.initialize();
...
```

Instead of doing this (the old way): 

```java 
InputStream stream = ClassLoader.getSystemResourceAsStream(propsFile);
JWNL.initialize(stream);
...
```

All other functionalities are untouched.

If you want to see what kind of stuff can be done with WN, checkout [this exampe file](src/main/java/net/didion/jwnl/Examples.java)!

Happy WordNet-ing! :) 

