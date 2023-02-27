# Introduction
Non-blocking, reactive client to perform HTTP requests, exposing a fluent, reactive API over underlying HTTP client libraries such as Reactor Netty. Use static factory methods create() or create(String) , or builder() to prepare an instance.

# Three Steps for working with Webclient-
  1. Creating a webClient Instance
  2. Preparing the request
  3. Reading the response
  
  ### Creating a WebClient Instance
  ```java
    WebClent webClient = WebClient.create();
    
    WebClient webClient = WebClient.create("http://localhost:8080");
    
    WebClient webClient = Webclient.builder()
      .baseUrl("http://localhost:8080")
      .defaultHeader()
      .build();

    WebClienr webClient8081 = WebClient.mutate()
      .baseUrl("http://localhost:8081")
      .build();
  ```
  
  ### Preparing the request
  ```java
    Product product = ...
    webClient
      .get() //Webclient.ReqestHeadersUriSpec
      .uri("/products/{id}", id)//WebClient.UriSpec
      .accept(MediaType.APPLICATION_JSON);
    
    webClient
      .post()
      .uri("/products")
      .contentType(MediaType.APPLICATION_JSON)
      .bodyValue(product);
  ```
  ### Reading the response
  ```java
    Mono<Product> mono = 
      webClient
        .get()
        .uri("/products/{id}", id)
        .retrieve()
        .bodyToMono(Product.class);
  ```
