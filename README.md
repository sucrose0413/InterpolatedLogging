# Interpolated Logging

**Extensions to Logging Libraries to write Log Messages using Interpolated Strings without losing Structured Property Names**

Most logging libraries support **structured logging**:

```cs
logger.Info("User {UserName} created Order {OrderId} at {Date}, operation took {OperationElapsedTime}ms", 
    name, orderId, DateTime.Now, elapsedTime);
```

This means that our logs will get not only plain strings but also the structured data, allowing us to search for specific property values (e.g. search for `OrderId="123"` to trace some order, or search for `OperationElapsedTime>1000` to find slow operations).  

The problem with this approach is that it's easy to put the wrong number of parameters or wrong order of parameters.

If you just use regular interpolated strings you lose the benefit of structured logging, since the logging library won't know the names of each property:

```cs
logger.Info($"User {UserName} created Order {OrderId} at {Date}, operation took {OperationElapsedTime}ms");
```

This library solves this problem by creating extensions to popular logging libraries which allow us to use string interpolation (easier to write) and yet set the name of the properties:

```cs
logger.InterpolatedInfo($"User {new { UserName = name }} created Order {new { OrderId = orderId}} at {new { Date = now }}, operation took {new { OperationElapsedTime = elapsedTime }}ms");
```


# Collaborate

This is a brand new project, and your contribution can help a lot.  

**Would you like to collaborate?**  

Please submit a pull-request or if you prefer you can [create an issue](https://github.com/Drizin/InterpolatedLogging/issues) or [contact me](http://drizin.io/pages/Contact/) to discuss your idea.

## License
MIT License
