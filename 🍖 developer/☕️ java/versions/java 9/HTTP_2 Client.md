
[[🧁 Java9]]

A new way of performing HTTP calls arrives with Java 9. As existing or Legacy HTTP Client API has numerous issues (like supports HTTP/1.1 protocol and does not support HTTP/2 protocol and WebSocket, works only in Blocking mode and lot of performance issues.), they are replacing this HttpURLConnection API with new HTTP client. They are going to introduce new HTTP 2 Client API under “java.net.http” package. It supports both HTTP/1.1 and HTTP/2 protocols. It supports both Synchronous (Blocking Mode) and Asynchronous Modes. It supports Asynchronous Mode using WebSocket API.

HttpClient client = HttpClient.newHttpClient();  
  
HttpRequest req =  
   HttpRequest.newBuilder(URI.create("http://www.google.com"))  
              .header("User-Agent", "Java")  
              .GET()  
              .build();  
  
HttpResponse resp = client.send(req, HttpResponse.BodyHandler.asString());

### HTTP Client in Java 11

The [new HTTP client](https://www.baeldung.com/java-9-http-client) from the _java.net.http_ package was introduced in Java 9. It has now become a standard feature in Java 11.

**The new HTTP API improves overall performance and provides support for both HTTP/1.1 and HTTP/2:**

```java
HttpClient httpClient = HttpClient.newBuilder()
  .version(HttpClient.Version.HTTP_2)
  .connectTimeout(Duration.ofSeconds(20))
  .build();
HttpRequest httpRequest = HttpRequest.newBuilder()
  .GET()
  .uri(URI.create("http://localhost:" + port))
  .build();
HttpResponse httpResponse = httpClient.send(httpRequest, HttpResponse.BodyHandlers.ofString());
assertThat(httpResponse.body()).isEqualTo("Hello from the server!");
```