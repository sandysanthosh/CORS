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
