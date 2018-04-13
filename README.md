# swagger-java-client

## Requirements

Building the API client library requires [Maven](https://maven.apache.org/) to be installed.

## Installation

To install the API client library to your local Maven repository, simply execute:

```shell
mvn install
```

To deploy it to a remote Maven repository instead, configure the settings of the repository and execute:

```shell
mvn deploy
```

Refer to the [official documentation](https://maven.apache.org/plugins/maven-deploy-plugin/usage.html) for more information.

### Maven users

Add this dependency to your project's POM:

```xml
<dependency>
    <groupId>io.swagger</groupId>
    <artifactId>swagger-java-client</artifactId>
    <version>1.0.0</version>
    <scope>compile</scope>
</dependency>
```

### Gradle users

Add this dependency to your project's build file:

```groovy
compile "io.swagger:swagger-java-client:1.0.0"
```

### Others

At first generate the JAR by executing:

    mvn package

Then manually install the following JARs:

* target/swagger-java-client-1.0.0.jar
* target/lib/*.jar

## Getting Started

Please follow the [installation](#installation) instruction and execute the following Java code:

```java

import io.swagger.client.*;
import io.swagger.client.auth.*;
import io.swagger.client.model.*;
import io.swagger.client.api.BlogpostApi;

import java.io.File;
import java.util.*;

public class BlogpostApiExample {

    public static void main(String[] args) {
        
        BlogpostApi apiInstance = new BlogpostApi();
        BlogPost body = new BlogPost(); // BlogPost | New blog post
        try {
            BlogPost result = apiInstance.addBlogPost(body);
            System.out.println(result);
        } catch (ApiException e) {
            System.err.println("Exception when calling BlogpostApi#addBlogPost");
            e.printStackTrace();
        }
    }
}

```

## Documentation for API Endpoints

All URIs are relative to *http://localhost:8080/my-blog-service/v1*

Class | Method | HTTP request | Description
------------ | ------------- | ------------- | -------------
*BlogpostApi* | [**addBlogPost**](docs/BlogpostApi.md#addBlogPost) | **POST** /blog | Add a blog post
*BlogpostApi* | [**deleteBlogPost**](docs/BlogpostApi.md#deleteBlogPost) | **DELETE** /blog/{id} | Deletes a blog post
*BlogpostApi* | [**getBlogPostById**](docs/BlogpostApi.md#getBlogPostById) | **GET** /blog/{id} | Find blog post by ID
*BlogpostApi* | [**updateBlogPost**](docs/BlogpostApi.md#updateBlogPost) | **PUT** /blog | Update an existing blog post


## Documentation for Models

 - [BlogPost](docs/BlogPost.md)


## Documentation for Authorization

All endpoints do not require authorization.
Authentication schemes defined for the API:

## Recommendation

It's recommended to create an instance of `ApiClient` per thread in a multithreaded environment to avoid any potential issues.

## Author

support@my-blog-service.com

