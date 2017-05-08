# Properties
- Getters and setters...write your own or built in?
- Backing variables?
- Computed properties?

## C# Properties
>A property is a member that provides a flexible mechanism to read, write, or compute the value of a private field. Properties can be used as if they are public data members, but they are actually special methods called accessors. This enables data to be accessed easily and still helps promote the safety and flexibility of methods.
>Properties can  be read-write (they have both a get and a set accessor), read-only (they have a get accessor but no set accessor), or write-only (they have a set accessor, but no get accessor).

Getters and setters can be auto-implemented in C or you can provide your own implementation. the compiler will create backing properties automatically for each auto-implemented property.

You can use a private backing field to implement a property. The get and set accesor can provide date validation or manipulation before setting or returning the property value.

The following example uses both auto-implemented accessors and ones you write your own with a private backing field.
```csharp
using System;

class TimePeriod
{
  //private backing field.
   private double seconds;

   //public property that does the conversion from Hours to seconds
   public double Hours
   {
       get { return seconds / 3600; }
       set {
          if (value < 0 || value > 24)
             throw new ArgumentOutOfRangeException(
                   $"{nameof(value)} must be between 0 and 24.");

          seconds = value * 3600;
       }
   }
}

class SimpleClass {
  //read-only Properties can be done by making the set private
  public string Sample = {get; private set;}
  //auto-implemented read-write property
  public string Mutable = {get; set;}

  public SimpleClass(string s1, string s2) {
    sample = s1;
    mutable = s2;
  }
}
class Program
{
   static void Main()
   {
       TimePeriod t = new TimePeriod();
       SampleClass s = new SampleClass("read-only", "mutable");
       s.Mutable = "Changed";
       // The property assignment causes the 'set' accessor to be called.
       t.Hours = 24;

       // Retrieving the property causes the 'get' accessor to be called.
       Console.WriteLine($"Time in hours: {t.Hours}");
       Console.WriteLine($"SampleClass s.Mutable: {s.Mutable} s.Sample: {s.Sample}");
   }
}
// The example displays the following output:
//    Time in hours: 24
// SampleClass s.Mutable: changed s.Sample: read-only
```

C# can have calculated properties by implementing the calculations in the get accessor.
```csharp
public class WorkOrder
{
    public int LaborHours { get; set; }
    public decimal LaborRate { get; set; }

    //LaborCost is a calculated property
    public decimal LaborCost
    {
        get
        {
            return LaborHours * LaborRate;
        }
    }
}
```

### References
(https://docs.microsoft.com/en-us/dotnet/articles/csharp/programming-guide/classes-and-structs/properties)

# Ruby Properties
In ruby all instance variables are always private. Accessor methods are not provided by default.

An Example of accessor
```ruby
class Fruit
       def kind=(k)
         @kind = k
       end
       def kind
         @kind
       end
     end
f2 = Fruit.new
f2.kind = "banana"
puts f2.kind
# outputs banana
```
Alternatively, ruby provides a short hand for writing accessors

Shortcut | effect  
attr_reader :v	| def v; @v; end  
attr_writer :v	| def v=(value); @v=value; end  
attr_accessor :v	| attr_reader :v; attr_writer :v  
attr_accessor :v, :w	| attr_accessor :v; attr_accessor :w  

the following Example has the same effect as the one above.
```ruby
class Fruit
  attr_accessor :kind
end
f2 = Fruit.new
f2.kind = "banana"
puts f2.kind
# outputs banana
```

You can do computed properties by just implementing them in the getter
```ruby
class Fruit
       def kind=(k)
         @kind = k
       end
       def kind
         @kind
       end
       def kind_squared
         @kind * @kind
       end
     end
f2 = Fruit.new
f2.kind = 2
puts f2.kind_squared
# outputs 4
```
### REFERENCES
(http://www.rubyist.net/~slagell/ruby/accessors.html)

[Back to the Home Page](https://github.com/ersggb/CSharpvsRuby)
