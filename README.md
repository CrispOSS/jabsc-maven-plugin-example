# jabsc-maven-plugin-example

This module provides an example on how to use jabsc (ABS Compiler to Java) and jabsc-maven-plugin (Maven Plugin for jabsc). 

## Requirements

* Java 8
* Apache Maven 3.3.x

## Getting Started

Simply fork this repository and start developing!

## Configure `pom.xml`

### Add jabsc-maven-plugin

The jabsc-maven-plugin can be configured as:

```xml
         <plugin>
            <groupId>com.github.crisposs</groupId>
            <artifactId>jabsc-maven-plugin</artifactId>
            <version>${version.jabsc-maven-plugin}</version>
            <executions>
               <execution>
                  <id>abs-compile</id>
                  <phase>generate-sources</phase>
                  <goals>
                     <goal>jabsc</goal>
                  </goals>
               </execution>
            </executions>
         </plugin>
```

where latest `${version.jabsc-maven-plugin}` is ![Maven Central](https://img.shields.io/maven-central/v/com.github.crisposs/jabsc-maven-plugin.svg?style=flat-square).

### Optional explicit dependencies

You can define the following dependencies *explicitly* in `pom.xml` which would override the dependencies coming from the plugin itself:

```xml
      <dependency>
         <groupId>${project.groupId}</groupId>
         <artifactId>abs-api</artifactId>
         <version>${version.abs-api}</version>
      </dependency>
      <dependency>
         <groupId>${project.groupId}</groupId>
         <artifactId>jabsc</artifactId>
         <version>${version.jabsc}</version>
      </dependency>
```

where latest `${version.abs-api}` is ![Maven Central](https://img.shields.io/maven-central/v/com.github.crisposs/abs-api.svg?style=flat-square) and latest `${version.jabsc}` is ![Maven Central](https://img.shields.io/maven-central/v/com.github.crisposs/jabsc.svg?style=flat-square).

### ABS sources

By default jabsc-maven-plugin compiles all ABS sources from `src/main/abs`. An example can be found at [TestInterface.abs][1].

### Maven Build Lifecycle

The jabsc-maven-plugin hooks into standard Maven life cycle at `generate-sources` phases. Consequently, all the generated Java files from your ABS sources will be compiled by Maven in any phase/goal that would require compiling sources.

### IDE Integration

To integrate with eclipse, simply run:

```bash
$ mvn eclipse:eclipse -DdownloadSources=true
```

You will see a new "source folder" appearing on your eclipse project with name `target/generated-sources/jabsc`.

[1]: src/main/abs/TestInterface.abs
