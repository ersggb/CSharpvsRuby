C#

Lambdas explained
> C# uses lambda expressions to create delegates or expression tree types.
> To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator =>, and you put the expression or statement block on the other side.

Assigning a lambda expression to a delegate:
delegate int del(int i);  
static void Main(string[] args)  
{  
    del myDelegate = x => x * x;  
    int j = myDelegate(5); //j = 25  
}  

Assigning a lambda expression to an expression tree type:
using System.Linq.Expressions;  

namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Expression<del> myET = x => x * x;  
        }  
    }  
}

Closures explained
> The C# compiler detects when a delegate forms a closure which is passed out of the current scope and it promotes the delegate, and the associated local variables into a compiler generated class

static void Main(string[] args)
{
    var inc = GetAFunc();
    Console.WriteLine(inc(5));
    Console.WriteLine(inc(6));
}
 
public static Func<int,int> GetAFunc()
{
    var myVar = 1;
    Func<int, int> inc = delegate(int var1)
                            {
                                myVar = myVar + 1;
                                return var1 + myVar;
                            };
    return inc;
}

Ruby

In Ruby, lambdas are closures.

> Lambdas enforce the correct number of arguments
> Lambdas support default arguments
> Lambdas can be computed hashes and arrays
> Lambdas have built-in currying
> Lambdas are a special kind of Proc

>To create lambdas in Ruby:
> lambda = lambda {}
> lambda = ->() {}

