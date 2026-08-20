# Lisp Interpreter in Python

Reads Lisp source, tokenises it, parses it into nested expressions, and evaluates them.

## What it supports

- **Types:** integers, floats, strings, symbols
- **Special forms:** `lambda`, `define`, `if`
- **Primitives:** arithmetic and comparison operators
- **Closures:** lambdas capture their defining environment
- **Environments:** nested scope with lookup falling through to the parent

## Usage

Run a source file:

```bash
python interpreter.py program.lisp
```

Or start the REPL:

```bash
python interpreter.py
```

```
lisp> (+ 1 2)
3
lisp> (define square (lambda (x) (* x x)))
lisp> (square 7)
49
lisp> exit
Goodbye!
```

## How it works

```
source text
    │
    ▼
tokenize()      character-level scan; handles parentheses, whitespace
    │           and quoted strings as single tokens
    ▼
parse()         builds nested Python lists mirroring the S-expression tree
    │
    ▼
eval()          walks the tree against an environment, dispatching on
    │           special forms before falling through to function application
    ▼
result
```


