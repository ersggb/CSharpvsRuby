# Referencing Instance in C# and Java

## C#
C# uses this to reference objects from themselves
``` C#

public Light(Vector v)
{
    this.dir = new Vector(v);
}
```

## Ruby

Ruby uses self to reference objects from themselves
``` ruby
class Foo
  attr_writer :bar
  def do_something
    self.bar = 2
  end
end
```
