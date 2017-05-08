## Reflection
> Reflection allows for the inspection of code at runtime without knowing the names of methods, classes, or functions.

# C#
> The System.Reflection namespace contains classes and interfaces that provide a managed view of loaded types, methods, and fields, with the ability to dynamically create and invoke types. When writing a C# code that uses reflection, the coder can use the typeof operator to get the object's type or use the GetType() method to get the type of the current instance.
```C#
int i = 42;  
System.Type type = i.GetType();  
System.Console.WriteLine(type); 
```
This code would return System.Int32

# Ruby
> Ruby has multiple ways of inspecting/reflecting its code.
```ruby
o.class
o.superclass
o.is_a?
o.kind_of?
o.respond_to?
o.local_variables
o.global_variables
o.instance_variables
o.methods
```

These all will return the result of the query and you can use this info to build a model of the class without any access to source.
