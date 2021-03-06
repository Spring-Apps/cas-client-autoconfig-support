cas-client-autoconfig-support
=============================

Library providing annotation-based configuration support for CAS Java clients. Primarily designed for super easy CASification of Spring Boot apps.

> This project was developed as part of Unicon's [Open Source Support program](https://unicon.net/opensource).
Professional Support / Integration Assistance for this module is available. For more information [visit](https://unicon.net/opensource/cas).

## Current version
`1.0.0-M1`

## Usage

* Define a dependency:

> Maven:

  ```xml
  <dependency>
      <groupId>net.unicon.cas</groupId>
      <artifactId>cas-client-autoconfig-support</artifactId>
      <version>1.0.0-M1</version>
      <scope>runtime</scope>
  </dependency>
  ```

> Gradle:

  ```Groovy
  dependencies {
        ...
        runtime 'net.unicon.cas:cas-client-autoconfig-support:1.0.0-M1'
        ...
  }
  ```

* Add the following properties

> in Spring Boot's `application.properties` or `application.yml` Example:

```bash
   cas.server.url-prefix=https://my.cas.server/cas
   cas.client.service-url=https://this.protected.server/app
   #Optional. Defaults to /login
   cas.server.login-url=/login
```

* Annotate Spring Boot application (or any @Configuration class) with `@EnableCasClient` annotation

> For CAS protocol (authentication and validation filters) - which is default

```java
    @SpringBootApplication
    @Controller
    @EnableCasClient
    public class MyApplication { .. }
```

> For SAML protocol (authentication and validation filters)

```java
    @SpringBootApplication
    @Controller
    @EnableCasClient(validationType = EnableCasClient.ValidationType.SAML)
    public class MyApplication { .. }
```