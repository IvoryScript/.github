# Contributing to IvoryScript

Thank you for your interest in contributing to IvoryScript. The language is actively evolving, and all involvement — whether reporting a bug, suggesting a feature, improving documentation, or contributing code — is encouraged and appreciated.

---

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Ways to Contribute](#ways-to-contribute)
- [Getting in Touch](#getting-in-touch)
- [Reporting Bugs](#reporting-bugs)
- [Suggesting Features](#suggesting-features)
- [Contributing Code](#contributing-code)
- [Contributing to Documentation](#contributing-to-documentation)
- [Development Notes](#development-notes)
- [Style Guidelines](#style-guidelines)

---

## Code of Conduct

By participating in this project, you agree to engage respectfully and constructively. Please keep all discussions focused on the work, and be welcoming to contributors of all experience levels.

---

## Ways to Contribute

There are many ways to get involved with IvoryScript:

- **Bug reports** — something behaving unexpectedly in the language, console, `iss`, or `isss`
- **Feature suggestions** — ideas for new language features, standard library additions, or tooling
- **Code contributions** — fixes, improvements, or new functionality via pull request
- **Documentation** — corrections, clarifications, examples, or entirely new guides
- **Examples** — interesting scripts that showcase language features
- **Testing** — trying out beta features and reporting your findings

---

## Getting in Touch

The primary point of contact for IvoryScript is:

📧 [mail@ivoryscript.net](mailto:mail@ivoryscript.net)

For general discussion, questions, and updates, visit the [IvoryScript community page](https://ivoryscript.net/community).

Before opening an issue or pull request for a significant change, it is worth reaching out first to discuss the direction and avoid duplicated effort.

---

## Reporting Bugs

If you encounter unexpected behaviour, please open a GitHub issue and include as much of the following as possible:

1. **A minimal reproducing script** — the smallest IvoryScript snippet that triggers the problem
2. **Expected behaviour** — what you expected to happen
3. **Actual behaviour** — what happened instead, including any error output
4. **Environment** — whether you are using the [online console](https://ivoryscript.net/console), `iss`, or `isss`, and on which platform
5. **Version information** — if known

For `isss`-specific issues, please note that it is currently available as a Linux version only, and include your Linux distribution and version where relevant.

---

## Suggesting Features

Feature suggestions are very welcome. When opening a feature request, please:

- **Describe the problem** you are trying to solve, not just the solution
- **Provide examples** of what the syntax or behaviour might look like in IvoryScript
- **Note any interactions** with existing language features such as the type system, `Exp a` evaluation semantics, or pattern matching
- **Consider the language philosophy** — IvoryScript values explicit evaluation control and a small, principled core

If you are unsure whether a suggestion fits the language direction, send an email before opening an issue.

---

## Contributing Code

### 1. Fork and branch

Fork the repository and create a branch for your change:

```bash
git checkout -b fix/my-bug-fix
# or
git checkout -b feature/my-new-feature
```

### 2. Make your changes

Keep changes focused. A pull request should address one concern — a single bug fix, a single feature, or a set of closely related changes.

### 3. Test your changes

Before submitting, test your changes against the [online console](https://ivoryscript.net/console) or a local `iss` session. Include IvoryScript scripts that demonstrate correct behaviour where applicable.

### 4. Write clear commit messages

Use the present tense and be concise:

```
Fix evaluation order in nested Exp expressions
Add mapf example to getting-started guide
Correct type signature for foldl in module reference
```

### 5. Open a pull request

Push your branch and open a pull request against `main`. In the pull request description:

- Summarise what the change does and why
- Reference any related issues
- Include example scripts or output if relevant

Pull requests are reviewed by the core team. Feedback may be given and revisions requested before merging.

---

## Contributing to Documentation

Documentation contributions are particularly valuable. The IvoryScript docs cover:

| Document | Location | Focus |
|---|---|---|
| Getting Started | `docs/getting-started` | Console use, basic examples, core concepts |
| User Guide | `docs/user-guide` | Expression forms, best practices, advanced usage |
| Reference Manual | `docs/reference-manual` | Formal language syntax and semantics |
| Module Reference | `docs/module-reference` | Built-in and standard library modules |
| Applications | `docs/applications` | `iss` and `isss` usage |

When editing documentation:

- Ensure all IvoryScript code examples are correct and runnable
- Use explicit type signatures in examples — this is considered good practice in the language itself
- Keep language clear and consistent with the existing tone
- For the Reference Manual, note that changes touching formal semantics should be discussed with the core team first

---

## Development Notes

### Applications

IvoryScript ships with two command-line applications:

- **`iss`** (Ivory System Session) — reads and executes IvoryScript scripts from standard input, with support for multi-line scripts and `:file "<filename>"` loading
- **`isss`** (Ivory System Socket Server) — a long-running proxy server managing multiple client sessions backed by `iss` workers; currently Linux only

When contributing fixes or features to either application, please include notes on the protocol or CLI behaviour affected.

### Evaluation semantics

IvoryScript distinguishes strictly between evaluated and unevaluated expressions. The `Exp a` type and the `#!` reduction operator are central to this. When writing or reviewing code that touches evaluation, bear in mind:

- Literals have type `Exp τ` by default; prefixing with `#` yields a strict value of type `τ`
- No expression form performs reduction implicitly — all reduction is explicit
- The `Exp (Exp a)` nesting is valid and meaningful

Contributors working on the core language should be familiar with the [Reference Manual](https://ivoryscript.net/documents/reference-manual) semantics sections before proposing changes to evaluation behaviour.

---

## Style Guidelines

### IvoryScript code

- Always include type declarations for top-level and `let`-bound functions
- Use `--` for single-line comments and `{- -}` for block comments
- Prefer explicit `case` expressions over nested `if/then/else` for clarity
- Keep lambda abstractions `(\x -> ...)` concise; extract named functions when logic is non-trivial

### Prose and documentation

- Use British English spelling (e.g. *behaviour*, *colour*, *licence*)
- Refer to the language as **IvoryScript** (one word, capital I and S)
- Refer to the platform as **The Ivory System** or **IvorySystem**
- Code, type names, keywords, and operators should always appear in backtick formatting inline

---

## Questions

If you are unsure about anything, please reach out at [mail@ivoryscript.net](mailto:mail@ivoryscript.net) before investing significant time in a contribution. The team is happy to provide guidance.
