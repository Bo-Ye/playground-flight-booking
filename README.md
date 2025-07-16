# AI powered expert system demo

Spring AI re-implementation of https://github.com/marcushellberg/java-ai-playground

This app shows how you can use [Spring AI](https://github.com/spring-projects/spring-ai) to build an AI-powered system that:

- Has access to terms and conditions (retrieval augmented generation, RAG)
- Can access tools (Java methods) to perform actions (Function Calling)
- Uses an LLM to interact with the user

![alt text](diagram.jpg)

## Requirements

- Java 21+

## Running

- Run the app by running `Application.java` in your IDE or 
- `mvn spring-boot:run` in the command line.

### With Groq Chat

It reuses the OpenAI Chat client but pointed to the Groq endpoint

Add to the POM the Spring AI Open AI boot starter:

```xml
<dependency>
    <groupId>org.springframework.ai</groupId>
    <artifactId>spring-ai-openai-spring-boot-starter</artifactId>
</dependency>
<dependency>
    <groupId>org.springframework.ai</groupId>
    <artifactId>spring-ai-transformers-spring-boot-starter</artifactId>
</dependency>
```

Add the Groq configuraiton to the `applicaiton.properties`:

```
spring.ai.openai.api-key=${GROQ_API_KEY}
spring.ai.openai.base-url=https://api.groq.com/openai
spring.ai.openai.chat.options.model=llama3-70b-8192
```

## Build Jar

```shell
./mvnw clean install -Pproduction
```

```shell
java -jar ./target/playground-flight-booking-0.0.1-SNAPSHOT.jar
```