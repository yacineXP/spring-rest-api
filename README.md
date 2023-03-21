


<h1 align="center">
  <br>
<a  href="https://spring.io/"  target="_blank"  rel="noreferrer"> <img  src="https://www.vectorlogo.zone/logos/springio/springio-icon.svg"  alt="spring"  width="180"  height="180"/> </a>
  <br>
  Spring REST [Learning]
  <br>
  <br>
</h1>

<p align="center">
  <a href="#project-description">Project Description</a> |
  <a href="#tech-stack-and-libraries">Tech Stack and Libraries</a> |
  <a href="#how-it-works">How it Works</a> |
  <a href="#code-examples">Code Examples</a> |
  <a href="#acknowledgements">Acknowledgements</a>
</p>



<div id="project-description"></div>

## 🚀 Project Description
This project is based on the "Creating Rest Services" chapter of "Spring in Action" book, where I learned how to define REST endpoints in Spring MVC, use Spring Data repositories to automatically expose REST endpoints, and consume REST APIs.

<div id="tech-stack-and-libraries"></div>

## 🛠️ Tech Stack and Libraries
This project was built using the following tech stack and libraries:
- Java Spring
- Spring MVC
- Spring Data
- JUnit

<div id="how-it-works"></div>

## ⚙️ How it Works

This project uses Java Spring to provide RESTful endpoints for the Taco Cloud application. The endpoints are defined in Spring MVC controllers, which handle incoming HTTP requests and return the appropriate HTTP responses. Spring Data repositories are used to automatically expose REST endpoints for the Taco Cloud application's database entities.

<div id="code-examples"></div>

## 💻 Code Examples
An example of a Spring MVC controller method that handles an incoming HTTP request to retrieve a Taco by its ID:
```java
@GetMapping("/{id}")
public ResponseEntity<Taco> tacoById(@PathVariable("id") Long id) {
    Optional<Taco> optTaco = tacoRepository.findById(id);
    if (optTaco.isPresent()) {
        return new ResponseEntity<>(optTaco.get(), HttpStatus.OK);
    }
    return new ResponseEntity<>(null, HttpStatus.NOT_FOUND);
}
```
In this code example, the @GetMapping("/{id}") annotation specifies that this method should handle incoming HTTP GET requests with a path that includes a variable id. The tacoRepository.findById(id) method is used to retrieve the Taco with the specified ID from the database. If the Taco exists, it is returned in a ResponseEntity with an HTTP status code of 200 OK. If the Taco does not exist, a ResponseEntity with an HTTP status code of 404 NOT FOUND is returned instead.

<div id="acknowledgements"></div>

## 📚 Acknowledgements 
This project was created with the help of the book **"Spring in Action"** by **Craig Walls** and **Ryan Breidenbach**. Many of the concepts and techniques used in this project were learned from this valuable resource.

