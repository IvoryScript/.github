# IvoryScript

> The programming language for [The Ivory System](https://ivorysystem.net).

IvoryScript is a declarative, essentially functional programming language designed for efficient dynamic programming and data persistence.
With a clean, Haskell-inspired syntax and a small but powerful core, it provides precise control over when and how values are evaluated — making it well-suited to both application logic and persistent data modelling.

> *"Computer science has two and precisely two problems: the naming of values, and the time at which a value is bound to a name."*
> — Maurice Wilkes, Cambridge University, c. 1976

IvoryScript is a programming tool for both — and an expansion of the second: the time at which a value is reduced to a simpler form.

---

## Features

| Feature | Description |
|---|---|
| **First-class names and types** | Efficient handling of dynamically typed values and binding names |
| **On-demand data** | Separate `Exp a` types for unevaluated, deferred expressions |
| **No implicit evaluation** | Full control over when and how evaluation is performed |
| **Advanced pattern matching** | Unrestricted data representation using constructor and deconstructor functions |
| **Pragmatic update** | Controlled mutability for reference values in an otherwise functional paradigm |
| **Multiple environments** | Native ability to interact with multiple environments |

---

## Quick Start

> IvoryScript is currently in **beta**. APIs may change before the stable 1.0 release.

### Try it online

The fastest way to get started is the **[IvoryScript online console](https://ivoryscript.net/console)** — no installation needed. Each session provides a clean, independent environment for script compilation, data, and execution.

### Hello, World

```ivory
"Hello, world"
```

Or using string concatenation:

```ivory
"Hello" ++ ", world"
```

Or via the `Show` class method:

```ivory
show "Hello, world\n"
```

### A Taste of IvoryScript

**Type declarations and functions**

```ivory
-- greet :: String -> String
let {
   greet :: String -> String;
   greet name = "Hello, " ++ name ++ "!"
} in
   greet "IvoryScript"
-- => "Hello, IvoryScript!"
```

**Function application** — no parentheses or commas needed:

```ivory
-- addInt :: Int -> Int -> Int
addInt 3 5
-- => 8
```

**Pattern matching with `case`**

```ivory
let {
   describeNumber :: Int -> String;
   describeNumber n = case n of {
      0 -> "Zero";
      1 -> "One";
      otherwise -> "Other"
   }
} in
   describeNumber 1
-- => "One"
```

**Currying and partial application**

```ivory
let {
   add :: Int -> Int -> Int;
   add x y = x + y;

   add3 :: Int -> Int;
   add3 x = add x 3
} in
   add3 5
-- => 8
```

**On-demand (unevaluated) data** — work with potentially infinite sequences:

```ivory
let {
   listFrom :: Int -> Int -> Exp [Int];
   listFrom s step = s :+ (listFrom (s + step) step);
   infiniteList = listFrom 1 1
} in
   take 10 infiniteList
-- => [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

**Controlled mutability via pointers**

```ivory
let x :: Ptr Int = ^0 in {
   show (@x); show '\n';  -- 0
   x @= 42;
   show (@x); show '\n';  -- 42
}
```

---

## Documentation

Full documentation is available at [ivoryscript.net/documents](https://ivoryscript.net/documents):

- **[Getting Started](https://ivoryscript.net/documents/getting-started)** — console access, basic examples, and core concepts
- **[Reference Manual](https://ivoryscript.net/documents/reference-manual)** — complete language specification: types, expressions, patterns, modules, and semantics

---

## Roadmap

| Milestone | Status |
|---|---|
| Core language spec | ✅ Complete |
| Standard library | ✅ Complete |
| Online console | ✅ Live |
| Beta release | 🔄 In progress |
| Stable 1.0 release | 🔜 Coming soon |
| Tooling (LSP, formatter) | 📅 Planned |
| Package registry | 📅 Planned |

---

## Contributing

IvoryScript is approaching its stable release and welcomes early contributors.

1. **Fork** this repository
2. **Create** a feature branch (`git checkout -b feature/my-feature`)
3. **Commit** your changes (`git commit -m 'Add my feature'`)
4. **Push** and open a **Pull Request**

Please read [CONTRIBUTING.md](CONTRIBUTING.md) before submitting. All contributors are expected to follow our [Code of Conduct](CONTRIBUTING.md#code-of-conduct).

---

## 🔗 Related

- [IvorySystem](https://github.com/IvorySystem) — The platform IvoryScript powers
- [ivoryscript.net](https://ivoryscript.net) — Official website and documentation
- [Online Console](https://ivoryscript.net/console) — Try IvoryScript in your browser

---

## 📄 Licence

IvoryScript is released under the [MIT Licence](LICENCE).
