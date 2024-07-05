To create a simple Spring Boot application with a JSP view that uses Bootstrap for styling, and a REST controller to pass values to the JSP, you can follow these steps:

1. **Set Up Your Spring Boot Project:**

   Create a new Spring Boot project using Spring Initializr or your preferred IDE. Make sure to include the following dependencies:
   - Spring Web
   - Thymeleaf (optional, but for JSP support, you'll use `spring-boot-starter-web`)

2. **Configure JSP in Spring Boot:**

   In `application.properties`, configure the JSP view resolver:

   ```properties
   spring.mvc.view.prefix=/WEB-INF/views/
   spring.mvc.view.suffix=.jsp
   ```

3. **Create a Simple REST Controller:**

   Create a controller class to handle HTTP requests and responses.

   ```java
   package com.example.demo.controller;

   import org.springframework.stereotype.Controller;
   import org.springframework.ui.Model;
   import org.springframework.web.bind.annotation.GetMapping;

   @Controller
   public class MyController {

       @GetMapping("/hello")
       public String sayHello(Model model) {
           model.addAttribute("message", "Hello, Spring Boot with JSP!");
           return "hello";
       }
   }
   ```

4. **Create a JSP View:**

   Create a `hello.jsp` file in the `src/main/webapp/WEB-INF/views/` directory.

   ```jsp
   <%@ page contentType="text/html;charset=UTF-8" language="java" %>
   <!DOCTYPE html>
   <html>
   <head>
       <title>Hello Spring Boot</title>
       <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
   </head>
   <body>
       <div class="container">
           <div class="row">
               <div class="col-md-12">
                   <h1>${message}</h1>
               </div>
           </div>
       </div>
   </body>
   </html>
   ```

5. **Run Your Spring Boot Application:**

   Make sure your application class is set up to run as a Spring Boot application.

   ```java
   package com.example.demo;

   import org.springframework.boot.SpringApplication;
   import org.springframework.boot.autoconfigure.SpringBootApplication;

   @SpringBootApplication
   public class DemoApplication {
       public static void main(String[] args) {
           SpringApplication.run(DemoApplication.class, args);
       }
   }
   ```

6. **Test Your Application:**

   Run your application and navigate to `http://localhost:8080/hello` in your browser. You should see the message "Hello, Spring Boot with JSP!" styled with Bootstrap.

This example demonstrates a simple setup using Spring Boot, JSP, and Bootstrap to pass a value from the controller to the view. If you need more complex interactions or data passing, you can expand this setup with additional endpoints, services, and more advanced Bootstrap features.
