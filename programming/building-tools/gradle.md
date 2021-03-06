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
