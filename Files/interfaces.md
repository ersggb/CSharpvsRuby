Interfaces / protocols - Emma
What does the language support?
What abilities does it have?
How is it used?


C#
C# supports interfaces, not protocols.
>An interface contains definitions for a group of related functionalities that a class or a struct can implement.
By using interfaces, you can, for example, include behavior from multiple sources in a class.

interface IEquatable<T>
    {
        bool Equals(T obj);
    }
    
    public class Car : IEquatable<Car>
    {
      ....
    }
    
Ruby
Interfaces can be emulated in Ruby, but cannot be explicitly declared as they can in C#


module CSV

  def to_csv
    raise "Not implemented"
  end

  def from_csv(line)
    raise "Not implemented"
  end

end

class User
  include CSV

  def to_csv
    "#{@name},#{@age}"
  end

  def from_csv(line)
    parts = line.split(",")

    @name = parts[0]
    @age = parts[1]
  end

end
