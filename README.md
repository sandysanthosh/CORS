# CORS


#### Configuring CORS

```

@CrossOrigin
interface PersonRepository extends CrudRepository<Person, Long> {}


@CrossOrigin(origins = "http://domain2.example",
  methods = { RequestMethod.GET, RequestMethod.POST, RequestMethod.DELETE },
  maxAge = 3600)
interface PersonRepository extends CrudRepository<Person, Long> {}




```


####  Repository REST Controller Method CORS Configuration

```

@RepositoryRestController
public class PersonController {

  @CrossOrigin(maxAge = 3600)
  @RequestMapping(path = "/people/xml/{id}", method = RequestMethod.GET, produces = MediaType.APPLICATION_XML_VALUE)
  public Person retrieve(@PathVariable Long id) {
    // …
  }
}


```

####  Global CORS Configuration


```

@Component
public class SpringDataRestCustomization implements RepositoryRestConfigurer {

  @Override
  public void configureRepositoryRestConfiguration(RepositoryRestConfiguration config, CorsRegistry cors) {

    cors.addMapping("/person/**")
      .allowedOrigins("http://domain2.example")
      .allowedMethods("PUT", "DELETE")
      .allowedHeaders("header1", "header2", "header3")
      .exposedHeaders("header1", "header2")
      .allowCredentials(false).maxAge(3600);
  }
}


```
