# P
Welcome to Passerine!
Passerine is a small, concise, extensible programming language, powered by a VM written in Rust.
Inspired by Scheme, OCaml, and Wren.
Passerine supports (syntactically safe) macros, coroutines, anonymous functions, and the like.
Here's a sample:

```
-- Recursive Fibonacci in linear time (memoization)

-- All functions are anonymous
-- They just happen to have a name
memoized = f -> {
    -- Dictionary
    seen = {:}

    -- Implied return
    a -> {
        -- Pattern Matching
        match seen[a] {
            -- No null types
            (Some a) -> a
            None     -> {
                result = (f a)
                seen[a] = result
                result
            }
        }
    }
}

fib = memoized (
    n -> match n {
        -- Pattern guards
        s | s < 2 -> s
        e         -> (fib n - 2) + (fib n - 1)
    }
)
```

## Getting Started
If you just want to see what Passerine can do:

> NOTE: Passerine is in an early stage of development.

1. Clone this git repository.
2. Build p using cargo.
3. Run the CLI on one of the examples: `cargo run -- examples/hello_world.p`.

If you'd like to contribute:

1. Read `CONTRIBUTING.md`.
2. Get up Passerine using the above instructions
3. Open issues and pull requests disclosing bugs or implementing improvements

> Fun Note: I didn't have access to wifi when I wrote the compiler until version 0.5.0.
As such, this compiler was developed completely from memory, without access to the internet for any sort of anything - no Stack Overflow, no Rust documentation, etc.
If you see any obvious errata in the compiler design, open an issue or create a pull request.

# Roadmap
Version, ∆ Done, Milestone, -- Date

0. ∆ Start project
    1. ∆ Lexer
    2. ∆ Parser
    3. ∆ Bytecode generator
    4. ∆ VM
        1. ∆ Local Variables -- Today
        2. Block Statements
    5. Unary datatypes
        1. Numbers
        2. Strings -- This weekend (28M)
    6. Functions
        1. Closures
        2. Tail Recursion
    7. Algebraic Datatypes (Tuple, Union, Struct, Map)
        1. Pattern Matching -- Next weekend (4A)
    7. Fibers
        1. Error Handling -- Weekend after (11A)
    8. CLI
    9. Standard Library
        1. Numeric Tower
    10. Clean up and optimize
1. First Stable Release -- Before May (2M)
    1. Tests
    2. Documentation Generation
    3. Package Manager
2. Macros + Backwards-Compatibility Breaking-Changes (BCBC)
3. Parallelism
4. TBD
