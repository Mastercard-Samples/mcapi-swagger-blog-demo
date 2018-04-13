## Prerequisites
The steps below outline how to install and use Swagger Codegen on a Mac environment with Homebrew. Refer to the official 
[Swagger Editor Documentation](https://swagger.io/docs/swagger-tools/#installation-11) for other install options. 

You will need the following installed:
* Java 7 or higher
* Maven 
* NPM
* NodeJS


## Install swagger-codegen:

```shell
brew install swagger-codegen
```

## Usage

### Client SDK
Generate the SDK with the following command:
```shell
swagger-codegen generate --input-spec my-blog-service.yaml --lang java --output generated-code --api-package com.blog.api --model-package com.blog.model
```
This will generate your SDK in a folder called `generated-code`. Review the file `README.md` within that folder for
instructions on how to integrate the SDK into your own project.

Use Maven and the generated `POM.xml` to execute the tests:
```shell
mvn -f generated-code/pom.xml test
``` 
These tests don't do anything yet, but you can modify them at a later stage to test against your server.

Install this package into your local Maven repo:
```shell
cd generated-code
mvn install
```

### Server Stub
Generate a NodeJS Server with the following commmand:
```shell
swagger-codegen generate -i my-blog-service.yaml -l nodejs-server -o server
```
This will generate your code in a folder `server`. Review the file `README.md` folder with that folder.

Use the following command to run the server:
```shell
cd server
npm start
```
This starts up a server on port 8080. The server comes with Swagger UI (see startup logs for URL), where you can try out
your server.

### Test Client and Server
Your SDK code will be configured to run API calls against the `host` value in our Swagger specification, in this case 
our NodeJS server on localhost port 8080. 

Create a new Java project and add your new client as a dependency. See `README.md` in the `generated-code` folder for 
details on how to do this.

Add the following code, which will call your NodeJS server to create a new blog post:
```
public static void main(String[] args) {
    BlogpostApi apiInstance = new BlogpostApi();
    BlogPost request = new BlogPost();
    request.setTitle("My blog title");
    request.setBody("This is my sample blog post");
    try {
        BlogPost response = apiInstance.addBlogPost(request);
        System.out.println(response);
    } catch (ApiException e) {
        System.err.println("Exception when calling BlogpostApi#addBlogPost");
        e.printStackTrace();
    }
}
```
If everything goes to plan, you will see the following in the console:
```shell
class BlogPost {
    id: 1
    title: My Blog Post
    body: This is my blog about Swagger
}
```

