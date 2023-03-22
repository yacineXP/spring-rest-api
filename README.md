


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
**1. An exemple of the tacoController:**
```java
@RestController
@RequestMapping(path="/api/tacos",                
                produces="application/json")
@CrossOrigin(origins="http://localhost:8080")       
public class TacoController {
  private TacoRepository tacoRepo;

  public TacoController(TacoRepository tacoRepo) {
    this.tacoRepo = tacoRepo;
  }

  @GetMapping(params="recent")
  public Iterable<Taco> recentTacos() {            
    PageRequest page = PageRequest.of(
            0, 12, Sort.by("createdAt").descending());
    return tacoRepo.findAll(page).getContent();
  }

  @PostMapping(consumes="application/json")
  @ResponseStatus(HttpStatus.CREATED)
  public Taco postTaco(@RequestBody Taco taco) {
    return tacoRepo.save(taco);
  }

  @GetMapping("/{id}")
  public Taco tacoById(@PathVariable("id") Long id) {
    Optional<Taco> optTaco = tacoRepo.findById(id);
    if (optTaco.isPresent()) {
      return optTaco.get();
    }
    return null;
  }

}
```
The TacoController is a Spring REST controller that handles HTTP requests related to tacos. It is annotated with ```@RestController```, ```@RequestMapping```, and ```@CrossOrigin``` annotations. The ```@RestController``` annotation indicates that this class contains RESTful web service methods. The ```@RequestMapping``` annotation is used to map HTTP requests to the class level and ```@CrossOrigin``` is used to enable Cross-Origin Resource Sharing (CORS) for the web service.

The class has three methods for handling GET and POST requests. The ```recentTacos()``` method handles GET requests with the "recent" parameter and returns a list of the most recently added tacos. The ```postTaco()``` method handles POST requests with JSON data and saves the taco to the database. The ```tacoById()``` method handles GET requests with a specific ID parameter and returns the taco with that ID if it exists in the database.

<div id="acknowledgements"></div>

## 📚 Acknowledgements 
This project was created with the help of the book **"Spring in Action"** by **Craig Walls** and **Ryan Breidenbach**. Many of the concepts and techniques used in this project were learned from this valuable resource.

