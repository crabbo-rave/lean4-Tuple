# lean4-Tuple
Tuples for lean 4

# Use
Add the git repository to your `lakefile.lean`

# Syntax
Check `Examples.lean` for all the syntax.

To use tuples, at the top of your file, put 
```lean
import Tuple
open Tuple
```

The tuple syntax looks like this:
```lean
#eval ⟪1, 4, 2.4, 'X', [1, 2, 45]⟫ -- ⟪1, 4, 2.4, 'X', [1, 2, 45]⟫
#eval ⟪⟫ -- ⟪⟫
```

And are essentially a list of types:
```lean
-- cons 1 (cons 4 (cons 2.4 (cons (Char.ofNat 88) (cons [1, 2, 45] unit)))) 
-- : Tuple [Nat, Nat, Float, Char, List Nat]
#check ⟪1, 4, 2.4, 'X', [1, 2, 45]⟫ 
#check ⟪⟫ -- unit : Tuple []
```

You can get the length of them:
```lean
#eval ⟪⟫.length -- 0
#eval ⟪1⟫.length -- 1
#eval ⟪1, "4", #[1, 5, -2]⟫.length -- 3
```

As well as the head and tail:
```lean
#eval ⟪1, 2, 3⟫.head -- 1
#eval ⟪1, 2, 3⟫.tail -- ⟪2, 3⟫
```

Tuples are able to be used as function parameters and can be matched on:
```lean
def tuplePatternMatch (tup: Tuple [Nat, String]) :=
  match tup with
  | ⟪1, "2"⟫ => true
  | ⟪2, "1"⟫ => true
  | _ => false

#eval tuplePatternMatch ⟪1, "2"⟫ -- true
#eval tuplePatternMatch ⟪1, "3"⟫ -
```

Also getting the nth item, which still needs its own custom syntax and to work on bare tuples. This is the only way to get the nth element:
```lean
def tuplePatternMatch (tup: Tuple [Nat, String]) :=
  match tup with
  | ⟪1, "2"⟫ => true
  | ⟪2, "1"⟫ => true
  | _ => false

#eval tuplePatternMatch ⟪1, "2"⟫ -- true
#eval tuplePatternMatch ⟪1, "3"⟫ -
```
