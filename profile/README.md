# Coordinated Restore at Checkpoint (CRaC)

The CRaC (Coordinated Restore at Checkpoint) Project researches the coordination of Java programs with mechanisms to checkpoint (make an image of, snapshot) a Java instance while executing. Restoring from the image could solve some of the problems with the start-up and warm-up times. The primary aim of the Project is to develop a new standard mechanism-agnostic API to notify Java programs about the checkpoint and restore events. Other research activities will include, but will not be limited to, integration with existing checkpoint/restore mechanisms and development of new ones, changes to JVM and JDK to make images smaller and ensure they are correct.

## Read More About CRaC

* [crac.org](https://crac.org/)
* [OpenJDK CRaC Project](https://openjdk.org/projects/crac/)
* [CRaC documentation by Azul](https://docs.azul.com/core/crac/crac-introduction)

## Using CRaC in your Application

Use the [CRaC library](https://github.com/CRaC/org.crac) in your project to handle checkpoint creation and restore from a checkpoint.

```java
package my.app;

import org.crac.Context;
import org.crac.Core;
import org.crac.Resource;

public class MyClass implements Resource {

    public MyClass() {
        Core.getGlobalContext().register(this);
    }

    @Override
    public void beforeCheckpoint(Context<? extends Resource> context) {
        /* ... */
    }

    @Override
    public void afterRestore(Context<? extends Resource> context) {
        /* ... */
    }
}
```

## Example Implementation Repositories

* [Spring Boot](https://github.com/CRaC/example-spring-boot)
* [Quarkus](https://github.com/CRaC/example-quarkus)
* [Micronaut](https://github.com/CRaC/example-micronaut)
* [AWS Lambda](https://github.com/CRaC/example-lambda)
* [Jetty Server](https://github.com/CRaC/example-jetty)
* [XML Transform](https://github.com/CRaC/example-xml-transform)
