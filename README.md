# Simple maven archetype example.

## maven-archetype-sample application

#### This is an example of how to create new maven archetype.

Check the [maven guide](https://maven.apache.org/guides/mini/guide-creating-archetypes.html) also if you need some help. Some useful info can be found [here](https://maven.apache.org/archetype/archetype-models/archetype-descriptor/archetype-descriptor.html) .

*This example is pretty straightforward. You can start from the first commit and build/run the project to see which output you get; each next commit just add/change something with an explanation of what is going on.*

##### To be able to build/run :

```
> JDK 1.8+ should be fine :)
> Maven 3+ should work.

e.g. I am using  maven-archetype-plugin:3.0.1
```

##### First
* Checkout the code.
* `mvn clean install` on the root `pom.xml` to get `maven-archetype-sample-1.0-SNAPSHOT.jar` in your `.m2`
* Once this is done - you can use that archetype to generate your project structure.

##### Second
```
mvn archetype:generate                              \
-DarchetypeGroupId=com.ivk23.maven.archetype.sample \
-DarchetypeArtifactId=maven-archetype-sample        \ 
-DarchetypeVersion=1.0-SNAPSHOT                     \
-DgroupId=my.app.group.id                           \
-DartifactId=my-mew-app                             \
-Dversion=2.0.0-SNAPSHOT                            \
-DmyProjectName=HelloWorldArchetype                 \
-DinteractiveMode=false                          
```
*! To be able to run mvn you have to install and configure Maven, but that's another story.*

* Because the archetype you created is located in your local maven repo,
you have to provide `-DarchetypeGroupId` , `-DarchetypeArtifactId` , `-DarchetypeVersion` for `mvn archetype:generate` .
* `-DgroupId` , `-DartifactId` , `-Dversion` - these are *groupId, artifactId, version* of your future project.
* `-DmyProjectName` - this one is just to show that any params can be added (if they are declared in requiredProperties) when you generate the project and their values will be used somewhere in the generated project (hopefully this makes some sense ))).
* `-DinteractiveMode=false` - I am using it because the default value is `TRUE` and when this interactiveMode is turned on you need to type some stuff manually when the project is being generated (it can be groupId, artifactId or so, or you just need to press Y to continue. Find more in the documentation or use as it is.)

That's it. Each time you change the archetype (updating descriptor) - you need `mvn clean install` and `mvn archetype:generate ...` .

It is also possible to create multimodule project, but it's not here. Just don't have time. But it should be easy having this as an example.
