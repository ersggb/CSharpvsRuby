### C# and Ruby Class Comparisons

#### Defining
  ##### C#
  > In C# a class is defined by providing the acess modifier (public, private, protected, static, internal, or protected) internal), the word "class" and then the name of the class. Example below.
    
~~~~c#

using System;

namespace ProgrammingGuide
{
  // Class definition.
    public class DogClass
    {
      // Class Members
      // Class Methods
    }
}
~~~~

  #### Ruby
  > In Ruby a class is defined by the word "class" and followed by the class name, then "end" after all the methods are written. Example below.
  
```ruby

# dog.rb  
# define class Dog  
class Dog  
  # Class Variables
  # Class Methods
end  

```

#### Creating new instances

  #### C#
  
  ```c#
  
  DogClass dog = new DogClass();
  
  ```

  #### Ruby
  
  ```ruby
  
  doggo = Dog.new
  
  ```

#### Constructing/initializing

  #### C#
  
  ```c#
  
  class DogClass
  {
    public string name, breed;
    
    //constructor
    public DogClass()
    {
      name = "Bradley";
      Breed = "Corgi";
    }
   }
  
  ```
  
  #### Ruby
  
  ```ruby
  
  # dog.rb  
  # define class Dog  
  class Dog 
    #Constructor
    def initialize(name, breed)
      @dog_name = name
      @dog_breed - breed
    end
  end  
  
  # Create Objects
  doggo = Dog.new("Badley", "Corgi")
  
  ```
 
#### Destructing/de-initializing

  #### C#
  
  ```c#
  
  
  ```
  
  #### Ruby
  
  ```ruby
  
  
  ```
