# yak4j-xml

XML utilities.

[![Maven Central](https://img.shields.io/maven-central/v/com.github.ngeor/yak4j-xml.svg?label=Maven%20Central)](https://central.sonatype.com/artifact/com.github.ngeor/yak4j-xml)
[![build](https://github.com/ngeor/yak4j-xml/actions/workflows/build.yml/badge.svg)](https://github.com/ngeor/yak4j-xml/actions/workflows/build.yml)
[![javadoc](https://javadoc.io/badge2/com.github.ngeor/yak4j-xml/javadoc.svg)](https://javadoc.io/doc/com.github.ngeor/yak4j-xml)

## Usage

You can easily serialize and (de)serialize objects into XML with
`XmlSerializer`.

Any checked `JAXBException` will be wrapped inside the runtime (unchecked)
`XmlRuntimeException`.

```java
class Demo {
    void serialize() {
        XmlSerializer serializer = new XmlSerializer();
        String xml = serializer.serialize(myObject, MyObject.class);
    }
}
```

```java
class Demo {
    void deserialize() {
        XmlSerializer serializer = new XmlSerializer();
        String xml = "<MyObject><Name>hello, world</Name></MyObject>";
        MyObject myObject = serializer.deserialize(xml, MyObject.class);
    }
}
```

## Developer Tips

Upgrade maven properties:

```sh
mvn -Pgpg -Dmaven.version.ignore='.*-beta.*' versions:update-properties
```

Prepare a release:

```sh
mvn release:clean
mvn -DtagNameFormat='v@{project.version}' release:prepare
// alternatively to not push changes and also format the pom.xml again
mvn -DtagNameFormat='v@{project.version}' -DpushChanges=false -DcompletionGoals=validate release:prepare
mvn release:clean
```
