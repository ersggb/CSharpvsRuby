# Namespaces in Ruby and C# Comparison
  - How are name spaces implemented?
  - How are name spaces used?
## C# Namespaces    

>A namespace is designed for providing a way to keep one set of names separate from another.
>The class names declared in one namespace does not conflict with the same class names declared in another.

A namespace is defined as the following.
```csharp
namespace sample {
  //class definitions go here
}
```

To access a namespace enabled function or varible, prepend the namespace followed by a '.' and the item name.
```csharp
  sample.item_name;
```
Namespaces can be nested and the *global* namespace is the root for all namespaces.

Namespaces and types have unique titles described by fully qualified names that indicate a logical hierarchy. For example, the statement A.B implies that A is the name of the namespace or type, and B is nested inside it.

```csharp
//the fully qualified name follows the line as a comment
namespace N1     // N1
{
    class C1      // N1.C1
    {
        class C2   // N1.C1.C2
        {
        }
    }
    namespace N2  // N1.N2
    {
        class C2   // N1.N2.C2
        {
        }
    }
}
```
### The *Using* keyword

>The using keyword states that the program is using the names in the given namespace which allows you to forgo the the prepending of namespaces.

```csharp
using System

class TestClass {
  static void Main()
   {
     //When using System, we do not have to prepend the System namespace to access Console
      Console.WriteLine("Using System");
      //alternatively we could use the fully qualified names
      System.Console.WriteLine("Fully Qualified");
   }
}
```

You can define aliases for namespaces with the using keyword.
If a namespace you are using hides a namespace that is higher in the heirarchy, you can access this higher namespace by starting your search for the identifier from the global namespace by using *global::*
```csharp
using Alias = System.Console;

class TestClass
{
    static void Main()
    {

      //we know do not have to write System or Console.
        Alias.WriteLine("Hello");

      //use of global keyword
      global::System.Console.WriteLine("Howdy");
    }
}
```
### References
(https://docs.microsoft.com/en-us/dotnet/articles/csharp/programming-guide/namespaces/)
(http://www.tutorialspoint.com/csharp/csharp_namespaces.htm)
## Namespaces in Ruby

>Ruby uses modules as a way of grouping together methods, classes, and constants. Modules act as namespaces in Ruby.

Module constants are named just like class constants, with an initial uppercase letter. The method definitions look similar, too: Module methods are defined just like class methods.

As with class methods, you call a module method by preceding its name with the module's name and a period, and you reference a constant using the module name and two colons.

You can include modules in another file using the require keyword. require_relative requires the file relative to the current directory.

```ruby
#file is week.rb
module Week
  FIRST = "Sunday"
  LAST = "Saturday"
  def Week.length()
    puts "7 Days"
   end
end

#file is year.rb
module Year
  FIRST = 1
  LAST = 365
  def Year.length()
    puts "365 Days"
  end
end

#file is test.rb
# the .rb is not nessecary when using require
require_relative 'week'
require_relative 'year'

puts Week.FIRST
puts Year.FIRST
Year.length()
#will output 'Sunday 1 365 Days'
```

You can use the *include* keyword to embed one or more modules into a class. If you include more than one module into a class this is called a mixin and is similar to multiple inheritance which ruby does not support outright. If the modules are defined in a different file, then you must require them before including them. Additionally, including provides the module methods to instances of classes. If you wish the class to have the module methods you must *extend* the module.

Consider this example
```ruby
module A
   def a1
   end
   def a2
   end
end
module B
   def b1
   end
   def b2
   end
end

class Sample
include A
include B
   def s1
   end
end

#create a new instance of the Sample class
samp = Sample.new
samp.a1
samp.a2
samp.b1
samp.b2
samp.s1
```

### References
(http://www.tutorialspoint.com/ruby/ruby_modules.htm)
(http://www.rubyist.net/~slagell/ruby/modules.html)

[Back to the Home Page](https://github.com/ersggb/CSharpvsRuby)
