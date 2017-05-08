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
