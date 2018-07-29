# Logging
Notes on how java logging works


|-------|       |----------|       |---------------------|       |-----------|
|  App  |  -->  |  Logger  |  -->  |  Appender(handler)  |  -->  |  outside  |
|-------|       |----------|       |---------------------|       |-----------|
                     |                   /     \      \
                  (Filter)           (Filter)(Filter) (Formatters/layouts)

- Logging is event based.
- A logger creates an event which is then passed
- onto a/multiple appenders which is then formatted using a formatter/layouts,
- Then the appender records the event to a destination depending on the type of appender (file, console etc)


Logging Frameworks
- Java provides a basic API for Logging in the java.util.logging package
- To really use logging properly, you would need to use a framework
- There are many frameworks such as Log4j, Logback, TinyLog
- Logback was based on Log4j 1
- Log4j 2 was an improvement in apis and performance when using the Disruptor library
- tinylog is really fast and recommended for small projects
- Apache commons logging and SLF4J are logging abstract layers which decouple the logging code from the logging framework
  - this allows you to switch the underlying logging framework
  - selecting an underlying framework is typically done at runtime using classpaths and configuration
  - if there are no frameworks available, then the typical behaviour is to disable all log calls

Configuration
- done via either xml, yml or properties files
- java.util.logging
  - uses logging.properties.
  - can be stored globally in JRE lib dir or per project
