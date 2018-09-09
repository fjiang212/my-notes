# Phases
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


# POM
## Aggregate and Parent POMs
https://www.smartics.eu/confluence/display/BLOG/2013/07/22/Using+Aggregate+and+Parent+POMs

* If your parent POM is also the aggregate POM, all projects are released simultaneously.
* A parent POM (that is not an aggregate POM) is released in its own cycle and owns an individual version number.
* An aggregate POM (that is not a parent POM) is never released and only acts as a build helper.
    * Use profiles to bundle projects
    * Use commandline options to build only part of the projects in the reactor.

 
## POM Best Practices
https://books.sonatype.com/mvnref-book/reference/pom-relationships-sect-pom-best-practice.html

## Differences between dependencymanagement and dependencies in maven
Dependency Management allows to consolidate and centralize the management of dependency versions without adding dependencies which are inherited by all children. This is especially useful when you have a set of projects (i.e. more than one) that inherits a common parent.
Another extremely important use case of dependencyManagement is the control of versions of artifacts used in transitive dependencies. 

# Maven Plugins
## Maven Eclipse plugins
Note: This plugin is retired. The Maven Eclipse Plugin is used to generate Eclipse IDE files (*.classpath, *.project, *.wtpmodules and the .settings folder) for use with a project.

Disclaimer: Users are advised to use m2e, the Eclipse Maven Integration instead of this plugin, as it can more closely resemble the actual build and runtime classpaths as described in the project pom.xml - among other advantages. 

## Spring Boot Maven Plugin
The Spring Boot Maven Plugin provides Spring Boot support in Maven, allowing you to package executable jar or war archives and run an application in-place.

The Spring Boot Plugin has the following goals.
* spring-boot:run runs your Spring Boot application.
* spring-boot:repackage repackages your jar/war to be executable.
* spring-boot:start and spring-boot:stop to manage the lifecycle of your Spring Boot application (i.e. for integration tests).
* spring-boot:build-info generates build information that can be used by the Actuator.

https://docs.spring.io/spring-boot/docs/current/maven-plugin/

# Links
* Maven repository search:###  https://mvnrepository.com/
* Maven Guide: https://maven.apache.org/guides/mini/index.html
* POM(Project Object Model) Reference: https://maven.apache.org/pom.html
* Maven Basic Tutorial: https://www.youtube.com/watch?v=al7bRZzz4oU&index=1&list=PL92E89440B7BFD0F6