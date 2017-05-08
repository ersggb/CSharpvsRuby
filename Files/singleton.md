# Singleton
- How is a singleton implemented?
- Can it be made thread-safe?
- Can the singleton instance be lazily instantiated?

## C# Singleton
Singletons can be implemented using lazy instantiation and thread  safe properties. The constructor must be private and the instance should be declared as volatile. An instance should be created only when the instance property is null otherwise the instance is returned.

This is an example
```csharp
using System;

public sealed class Singleton
{
   private static volatile Singleton instance;
   private static object syncRoot = new Object();

   private Singleton() {}

   public static Singleton Instance
   {
      get
      {
         if (instance == null)
         {
            lock (syncRoot)
            {
               if (instance == null)
                  instance = new Singleton();
            }
         }

         return instance;
      }
   }
}
```

This approach ensures that only one instance is created and only when the instance is needed. Also, the variable is declared to be volatile to ensure that assignment to the instance variable completes before the instance variable can be accessed. Lastly, this approach uses a syncRoot instance to lock on, rather than locking on the type itself, to avoid deadlocks.  
This double-check locking approach solves the thread concurrency problems while avoiding an exclusive lock in every call to the Instance property method. It also allows you to delay instantiation until the object is first accessed.
### References
(https://msdn.microsoft.com/en-us/library/ff650316.aspx)
## Ruby Singleton
It is simple to create a singleton in Ruby. You simply include the Singleton module in the standard library in the class you wish to make a singleton. Then you access the instance of the class though the instance method.
The singleton is created upon the first call to instance, thus it is lazily instantiated.
It should be thread safe.

```ruby
#simple singleton pattern in ruby
require 'singleton'

class AppConfig
  include Singleton
  attr_accessor :data

  def version
    '1.0.0'
  end
end
```
### References
(https://github.com/ruby/ruby/blob/trunk/lib/singleton.rb)
(https://www.sitepoint.com/design-patterns-in-ruby-observer-singleton/)

[Back to the Home Page](https://github.com/ersggb/CSharpvsRuby)
