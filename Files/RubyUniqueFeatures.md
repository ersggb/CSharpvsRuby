# Unique Features of Ruby

## Objects
> There are no primitave data types, everything is an object.

## Blocks
> Ruby has support for code blocks which can then be passed to functions as a parameter. This is useful for prioritizing when you write code. 

## Implicit Return
> If no return type is specified in a method, the compiler can often determine what should be returned. For example this code would return 8.
```ruby
def testMethod
    x = 4+4
  end
```

## Open
> In Ruby everything is open so you can extend any class or module.

## Method Indicators
> In Ruby the last character of a method name indicates its behaviour. If the method ends with a question mark, the return value is boolean. If the method ends with an exclamation the method can change the state of the object. In many cases a non exclamation version of the method is provided which modifies a copy of the object.
