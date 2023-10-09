# spring-data-mongodb-querydsl-processor

Java annotation processor provider for Spring Data MongoDB Querydsl processor.

Since ```spring-data-mongodb``` is missing service provider definition for ```org.springframework.data.mongodb.repository.support.MongoAnnotationProcessor```
maven QueryDSL annotation processing setup for ```spring-data-nongo``` is complicated and is not properly picked up by some IDE build system.
This library tries to solve this issue by ```javax.annotation.processing.Processor``` to solve this issue.

## Usage example

```xml

<build>
  <plugins>
    <plugin>
      <groupId>org.apache.maven.plugins</groupId>
      <artifactId>maven-compiler-plugin</artifactId>
      <version>3.11.0</version>
      <configuration>
        <annotationProcessorPaths>
          <path>
            <groupId>com.jyvee</groupId>
            <artifactId>spring-data-mongodb-querydsl-processor</artifactId>
            <version>1.0.0</version>
          </path>
          <path>
            <groupId>com.querydsl</groupId>
            <artifactId>querydsl-apt</artifactId>
            <version>5.0.0</version>
            <classifier>general</classifier>
          </path>
          <path>
            <groupId>org.springframework.data</groupId>
            <artifactId>spring-data-mongodb</artifactId>
            <version>4.1.4</version>
          </path>
        </annotationProcessorPaths>
      </configuration>
    </plugin>
  </plugins>
</build>
```

## Alternative

If you don't want to use this library, you can use ```org.springframework.data.mongodb.repository.support.MongoAnnotationProcessor``` directly.
In this case maven build will succeed, but IDE build system may not pick up annotation processor.

```xml

<build>
  <plugins>
    <plugin>
      <groupId>org.apache.maven.plugins</groupId>
      <artifactId>maven-compiler-plugin</artifactId>
      <version>3.11.0</version>
      <configuration>
        <annotationProcessors>
          org.springframework.data.mongodb.repository.support.MongoAnnotationProcessor
        </annotationProcessors>

        <annotationProcessorPaths>
          <path>
            <groupId>com.querydsl</groupId>
            <artifactId>querydsl-apt</artifactId>
            <version>5.0.0</version>
            <classifier>general</classifier>
          </path>
          <path>
            <groupId>org.springframework.data</groupId>
            <artifactId>spring-data-mongodb</artifactId>
            <version>4.1.4</version>
          </path>

        </annotationProcessorPaths>
      </configuration>
    </plugin>
  </plugins>
</build>
```
