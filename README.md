vaadin-custom-layout
==============

Template for a simple Vaadin application that only requires a Servlet 3.0 container to run.


Workflow
========

To compile the entire project, run "mvn install".

To run the application, run "mvn jetty:run" and open http://localhost:8080/ .

To produce a deployable production mode WAR:
- change productionMode to true in the servlet class configuration (nested in the UI class)
- run "mvn clean package"
- test the war file with "mvn jetty:run-war"

Client-Side compilation
-------------------------

The generated maven project is using an automatically generated widgetset by default. 
When you add a dependency that needs client-side compilation, the maven plugin will 
automatically generate it for you. Your own client-side customizations can be added into
package "client".

Debugging client side code
  - run "mvn vaadin:run-codeserver" on a separate console while the application is running
  - activate Super Dev Mode in the debug window of the application

Developing a theme using the runtime compiler
-------------------------

When developing the theme, Vaadin can be configured to compile the SASS based
theme at runtime in the server. This way you can just modify the scss files in
your IDE and reload the browser to see changes.

To use the runtime compilation, open pom.xml and comment out the compile-theme 
goal from vaadin-maven-plugin configuration. To remove a possibly existing 
pre-compiled theme, run "mvn clean package" once.

When using the runtime compiler, running the application in the "run" mode 
(rather than in "debug" mode) can speed up consecutive theme compilations
significantly.

It is highly recommended to disable runtime compilation for production WAR files.

Using Vaadin pre-releases
-------------------------

If Vaadin pre-releases are not enabled by default, use the Maven parameter
"-P vaadin-prerelease" or change the activation default value of the profile in pom.xml .C

How to create project on GitHub (linux)
=======================================

Create repository on github
---------------------------
```
git clone https://github.com/jakub-olszewski/vaadin-custom-layout.git
```
```
mvn archetype:generate -DarchetypeGroupId=com.vaadin -DarchetypeArtifactId=vaadin-archetype-application -DarchetypeVersion=8.1.6 -DgroupId=eu.b24u.vaadin -Dversion=0.1 -Dpackaging=war
```
Write: vaadin-custom-layout

Note:
* Latest version : https://mvnrepository.com/artifact/com.vaadin/vaadin-archetype-application
* in the same folder

Git - add and commit
--------------------
```
git add .
git config --global user.email "j.b.olszewski@gmail.com" 
git config --global user.name "jakub-olszewski" 
git commit -m "Init commit"
git push -u origin master
```
Git - use gitignore
-------------------
```
git rm -r --cached .
git add .
git status
```

External link
-------------
https://github.com/samie/VaadinTetris
