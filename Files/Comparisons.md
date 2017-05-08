Comparisons of references and values - Emma In Progress 🍎
How are values compared? (i.e. comparing two strings)

C#
To compare primitive datatypes, use ==
.Equals is used for reference equality for reference types, and bitwise equality for value types, but for objects and strings.
<, >, <=, >=, and != also can compare primitive datatypes.

Ruby
Ruby uses ==, <, >, <=, >=, and !=
> Ruby has <=> which is a comparison method or ‘spaceship method’. The method must return –1 when you think your current object is smaller than the one you’re comparing against. If you think it is larger you need to return +1, otherwise you return zero (the objects are equal)
