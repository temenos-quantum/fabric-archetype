# Fabric Maven Archetype

[Fabric](https://www.kony.com/products/fabric/) allows developers to write custom code in order to define [services](https://docs.kony.com/konylibrary/konyfabric/kony_fabric_user_guide/Default.htm#Java_Adapter.htm), [pre-processors and post-processors](https://docs.kony.com/konylibrary/konyfabric/kony_fabric_user_guide/Default.htm#Java_Preprocessor_Postprocessor_.htm).
This can either be done in [Java](https://docs.kony.com/konylibrary/integration/MiddlewareAPI) or Javascript.

For Java, writing custom code requires the creation of a Java project, which will in turn have to depend on libraries
provided by Fabric, and also extend specific classes from the Fabric middleware API.

This repository defines a [Maven archetype](https://maven.apache.org/guides/introduction/introduction-to-archetypes.html)
that serves as a template for creating a Java project, which already includes all the necessary dependencies and some
sample classes for custom Fabric services, pre-processors and post-processors.

As with all Maven archetypes, **the intent is that you use this to jumpstart your development**.

If you have already installed Maven, proceed to download (or clone) this project, and install this archetype and update the archetype catalog. 

```
git clone https://github.com/temenos-quantum/fabric-archetype.git
cd fabric-archetype
mvn install
mvn install archetype:update-local-catalog
```

Then change directory to where you wan to create the Fabric Java project and run:

```
mvn archetype:generate \
	-DarchetypeGroupId=com.kony \
	-DarchetypeArtifactId=fabric-archetype \
	-DarchetypeVersion=1.0-SNAPSHOT \
	-DgroupId=[your group id] \
	-DartifactId=[your project name]
```

Make sure you replace `[your group id]` with your company's group id —e.g. `com.acme`— and `[your project name]` with
the artefact id of your project —e.g. `HelloWorld`.

```
mvn archetype:generate \
	-DarchetypeGroupId=com.kony \
	-DarchetypeArtifactId=fabric-archetype \
	-DarchetypeVersion=1.0-SNAPSHOT \
	-DgroupId=com.acme \
	-DartifactId=HelloWorld

```

This will create the following project structure for you.

```
.
├── HelloWorld.iml
├── pom.xml
└── src
    ├── main
    │   └── java
    │       └── com
    │           └── acme
    │               ├── post
    │               │   └── TimestampPostProcessor.java
    │               ├── pre
    │               │   └── TimestampPreProcessor.java
    │               └── services
    │                   └── HelloWorldService.java
    └── test
        └── java
            └── com
                └── acme
                    ├── post
                    │   └── TimestampPostProcessorTest.java
                    ├── pre
                    │   └── TimestampPreProcessorTest.java
                    └── services
                        └── HelloWorldServiceTest.java
```

The resulting sample Java Maven project contains self-documented classes and a self-documented POM file, which you can modify to your project's needs. The project also contains sample test scripts using [TestNG](https://testng.org) and [Mockito](https://site.mockito.org).

As with all Maven projects, you'll be able to test it by running:
```
mvn test
```
or build the JAR file to upload into Fabric by running:
```
mvn package
```
