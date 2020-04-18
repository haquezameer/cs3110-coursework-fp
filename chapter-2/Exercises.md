# Exercises

```ocaml
7 * (1+2+3)

42
```

```ocaml
"CS " ^ string_of_int 3110

: string = "CS 3110"
```

Write an expression multiply 42 by 10

```ocaml
42 * 10;;
: int = 420
```

Expression divides 3.14 by 2.0

```ocaml
3.14 /. 2.0;;
: float = 1.57
```

Expression for 4.2 raised to power 7

```ocaml
4.2 ** float_of_int 7;;
: float = 23053.933...
```

Expression compare 42 to 42 structurally

```ocaml
42 = 42;;
: bool = true
```

Expression to compare "hi" to "hi" using structural and physical equality

```ocaml
"hi" = "hi";;
: bool = true

"hi" == "hi";;
: bool = false
```

Write an if expression that evaluates to 42 if 2 is greater than 1 and otherwise evaluates to 7.

```ocaml
let x = if 2 > 1 then 42 else 7;;
val : x int = 42
```

Define a function double that multiplies its input by 2. For example, double 7 would be 14. Test your function by applying it to a few inputs. Turn those test cases into assertions.

```ocaml
let double x = x * 2;;
val : double int -> int = <fun>

double 32;;
: int = 64

double 2;;
: int = 4
```

Define a function that computes the root-mean-square of two numbers—i.e.,  (x2+y2)/2

```ocaml
let rms (x: float) (y: float) : float = sqrt(( x ** 2.0 +. y ** 2.0) /. 2.0);;
val rms : float -> float -> float = <fun>

rms 2.0 4.0;;
- : float = 3.16227766016837952
```

Define a recursive function fib : int -> int

```ocaml
let rec fib n = if n = 0  then 0 else if n = 1 then 1 else fib (n - 1) + fib (n - 2);;
val fib : int -> int = <fun>

fib 2;;
- : int = 1
```

What is the type of each of the functions below? You can ask the toplevel to check your answers.

```ocaml
let f x = if x then x else x
val f : bool -> bool = <fun>

let g x y = if y then x else x
val g : 'a -> bool -> 'a = <fun>

let h x y z = if x then y else z
val h : bool -> 'a -> 'a -> 'a = <fun>

let i x y z = if x then y else y
val i : bool -> 'a -> 'b -> 'a = <fun>
```

Write a function divide : numerator:float -> denominator:float -> float. Apply your function.

```ocaml
let divide (numerator:float) (denominator:float) : float = numerator /. denominator;;
val divide : float -> float -> float = <fun>

divide 4.0 2.0;;
- : float = 2.
```

Which of the following produces an integer, which produces a function, and which produces an error? Decide on an answer, then check your answer in the toplevel.

```ocaml
add 5 1 // integer
add 5 // function
(add 5) 1 // integer
add (5 1) // error
```

Define an infix operator +/. to compute the average of two floating-point numbers.

```ocaml
let (+/.) (x: float) (y: float) : float = (x +. y) /. 2.0;;
val ( +/. ) : float -> float -> float = <fun>

1.0 +/. 2.0;;
- : float = 1.5
```

