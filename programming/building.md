# Table of Contents
1. [Maven](#maven)
2. [Gradle](#gradle)
3. [SBT](#sbt)

# Maven
## Phases
Maven Phases: The following are the most common default lifecycle phases executed.
* validate: validate the project is correct and all necessary information is available
* compile: compile the source code of the project
* **test**: test the compiled source code using a suitable unit testing framework. These tests should not require the code be packaged or deployed
* **package**: take the compiled code and package it in its distributable format, such as a JAR. 
* integration-test: process and deploy the package if necessary into an environment where integration tests can be run
* verify: run any checks to verify the package is valid and meets quality criteria
* **install**: install the package into the local repository, for use as a dependency in other projects locally
* deploy: done in an integration or release environment, copies the final package to the remote repository for sharing with other developers and projects.

There are two other Maven lifecycles of note beyond the default list above. They are
* clean: cleans up artifacts created by prior builds
* site: generates site documentation for this project

## Maven Plugins
### Maven Eclipse plugins
Note: This plugin is retired. The Maven Eclipse Plugin is used to generate Eclipse IDE files (*.classpath, *.project, *.wtpmodules and the .settings folder) for use with a project.

Disclaimer: Users are advised to use m2e, the Eclipse Maven Integration instead of this plugin, as it can more closely resemble the actual build and runtime classpaths as described in the project pom.xml - among other advantages. 

## Eclipse Maven Plugins
The goal of the **Eclipse m2e project** is to provide a first-class Apache Maven support in the Eclipse IDE, making it easier to edit Maven's pom.xml, run a build from the IDE and much more. For Java developers, the very tight integration with JDT greatly simplifies the consumption of Java artifacts either being hosted on open source repositories such as Maven Central, or in your in-house Maven repository.

## Links
* Maven repository search: https://mvnrepository.com/
* Maven Guide: https://maven.apache.org/guides/mini/index.html
* Maven Basic Tutorial: https://www.youtube.com/watch?v=al7bRZzz4oU&index=1&list=PL92E89440B7BFD0F6

# Gradle

# SBT
## Commands
Here are some of the most common sbt commands. For a more complete list, see https://www.scala-sbt.org/0.13/docs/Command-Line-Reference.html.

| Command | Note |
| -- | --- |
| clean |	Deletes all generated files (in the target directory). |
| compile |	Compiles the main sources (in src/main/scala and src/main/java directories). |
| test | Compiles and runs all tests. |
| console	| Starts the Scala interpreter with a classpath including the compiled sources and all dependencies. To return to sbt, type :quit, Ctrl+D (Unix), or Ctrl+Z (Windows). |
| run <argument>* |	Runs the main class for the project in the same virtual machine as sbt. |
| **package**	 | Creates a jar file containing the files in src/main/resources and the classes compiled from src/main/scala and src/main/java. |
| help <command> |	Displays detailed help for the specified command. If no command is provided, displays brief descriptions of all commands. |
| reload |	Reloads the build definition (build.sbt, project/*.scala, project/*.sbt files). Needed if you change the build definition. |
