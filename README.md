# SimpleHttpServer
You can easily set up a server on a local host.

## How to use
### Minimum Configuration

```java
// Import is omitted.

SimpleHttpServer server = new SimpleHttpServer(/*Priority ports for use*/ 8000);

server.serverStart();
```

### Set event handlers

```java
SimpleHttpServer server = new SimpleHttpServer(8000);

SimpleHttpEvent event = new SimpleHttpEvent(){
    /*
    Override event handler

    example:
    */

    @Override
    public String onPost(HttpExchange httpExchange, String body) 
    {
        System.out.println(body);
        return """
                Describe the response.
                If there is no response,specify null.
                """;
    }
}

server.serverStart(event);
```

### Change default method name

```java
SimpleHttpServer server = new SimpleHttpServer(8000);

SimpleHttpOption option = new SimpleHttpOption(){
    /*
    Override the method to change the default method name

    example:
    */

    @Override
    public String getPostMethodName() {
        /* 
        In this example,
        the name of the method received
        when the post is made is changed to [posts].
        */
        return "posts";
    }
};

server.serverStart(option);
```

### Combine options with previous events.

```java
SimpleHttpServer server = new SimpleHttpServer(8000);

// Events and options omitted

server.serverStart(event, option);
```

### Server Close

```java
/*
The process of starting the server is omitted.
The variable name of the server is [server].
*/

server.serverClose();
```

### Attention

If the port specified when defining the server is filled,
another random port will be used.
