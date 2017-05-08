### C# and Ruby Inheritance Comparison

  #### C#
  
  ```c#
  //parent class
  public class DogClass
  {
    public string name, breed;
    
    public DogClass()
    {
      name = "Bradley";
      breed = "Corgi";
    }
  }
  
  //extended class
  public class CorgiClass : DogClass
  {
    public bool derp, sploot;
    
    public CorgiClass()
    {
      name = "Greg";
      breed = "Corgi";
      derp = true;
      sploot = true;
    }
  }
  
  ```
  #### Ruby
  
  ```ruby
  
    class Dog  
      def bark  
        puts "bork"  
      end  
    end  
      
    class Corgi < Dog  
      def derp  
        puts "derp"  
      end  
    end  
      
    bradley = Corgi.new  
    bradley.bark  
    bradley.derp  
  
  ```
