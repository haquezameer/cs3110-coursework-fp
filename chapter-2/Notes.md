Functions

In Ocaml you define funcions is 

```ocaml
let inc x = x + 1
```

Here, `inc` is a function which increments its input by `1`.

If you define this function in utop, you will get output as:

```ocaml
val inc : int -> int = <fun>
```

See how great the type inference is? It automatically identifies that we are taking an input of type `int` and returning a output of type `int`.

In Ocaml functions do not necesaarily need to have a name that it is binded to. Functions without names are called Anonymous functions.

```ocaml
let inc = fun x -> x + 1
```

> Note the `fun` keyword

Function Application and Pipeline Operation

In Ocaml applying a function does not require a pair of parenthesis.

To apply `inc` fun on some input, we could simply do

```ocaml
inc 5
```

If you want to apply many functions together over some input, eg: You need to increment a number and then square it.

Assume you have a `square` function pre-defined, which takes an input and returns its square.

To do that, you can write it as:

```ocaml
square (inc 5)
```

Above expression first increments 5 and then uses that as input for `square`.

However, Ocaml provied a much elegent way to write this as follows:

```ocaml
5 |> inc |> square
```

In the above expression `|>` is called `pipeline operator`.
A pipeline operator literally performs a pipeline operation, i.e it pipes the data from left to right direction.

This syntax feels much natural and much more readable. It also shows the data flow much more clearly as the number of functions applied grows.

Compare 

```ocaml
square (inc (inc (square (inc 5))))
```

to

```ocaml
5 |> inc |> square |> inc |> inc |> square
```

Polymorphic Functions

A function which can be applied to many types of values is called a polymorphic function.

The identity function is the simplest polymorphic function.

You define an identity function as:

```ocaml
let id x = x
```

If you execute this on `utop`, you'll get an output like:
```ocaml
val id : 'a -> 'a = <fun>
```

Here, `'a` represents a type variable called alpha. It just signifies that the type is unknown.

More importantly, the expression shows us that an identity function recives a value of type `'a` and returns value of same type `'a`.

Partial Application

1.
```ocaml
let add x y = x + y
```

This function takes two arguments x and y and returns its sum.

However, there is another way to write it -

2.
```ocaml
let addx x = fun y -> x + y
```

Now you can use it as :

```ocaml
let add5 = addx 5
add5 2
```

This way you can `partially apply` the inputs, this is called partial application.

Something unique in ocaml is that both `1` & `2` are one and same, i.e even the function 
`add` can be used like we used `addx`.

```ocaml
let add5 = add 5
add5 2
```

This is because in ocaml both those function are syntatically different but sementically equivalent.
Every function even with multiple arguments, actually partially applying the arguments by returning a function that uses the previous argument.

This is something that I had a hard time understanding earlier as to why someone would do it this way,
but partially applying inputs makes composing functions very easy and also easy to reason about the data flow between those functions.

