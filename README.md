# programming-rust

* Setup
  * Rust
    * Rustup
      * Install
        * https://rustup.rs/
      * Update
        ```shell
        rustup update
        ```
      * Versions
        ```shell
        cargo --version
        rustc --version
        rustdoc --version
        ```
  * CLion
    * Indentation
      * CLion > Preferences > Editor > Code Style > Rust
* [Rust Standard Lib Docs](https://doc.rust-lang.org/)
  ```shell
  rustup doc --std
  ```
* Project
  * Create
    * Binary Executable
      ```
      cargo new --bin hello
      ```
    * Compile Executable in Target Directory
      ```
      cargo run arg1 arg2
      ```
    * Remove Executable
      ```
      cargo clean
      ```
    * Tests
      ```
      cargo test
      ```
* Code
  * Assertions
    * `assert!` - assert macro panic if argument not true
    * `debug_assert!` - skip assertion when program compiled for speed
  * Type Inference
  * Return Value of Expression
    * `;` - return value is last expression without semicolon
    * `return` - only for early returns
  * Types
    * Vec - `Vec` analogous to JS array
  * Variables
    * Mutability - `mut`
  * Loops
    * For - `for arg in std::env::args.skip(1) {` standard library returns different
    iterators that produce values to loop over. the first value returned by 
    this iterator is the name of the running program so we skip it.
  * Operators
    * `&` operator (i.e. `&x` borrows a reference to `x`)
      * iterating over a `Vec` (non-simple array value) of any size (i.e. `for m in &numbers[1..]`)
      requires developer control over memory consumption, release, and the lifetime 
      of each value, by informing Rust by using the `&` operator 
      that we are only "borrowing" a "reference" each element in succession from the
      `Vec` for the loop, but "ownership" of the `Vec` (`numbers`) remains with `numbers`.
    * `*` operator (i.e. `*x` is value associated with the reference `&x` has to `x`)
      * Dereferences the argument "reference" being iterated over to yield the value
      it refers to
  * Ownership
    * `numbers` variable "owns" the `Vec` for the scope then Rust automatically frees it.
     
  * Trait
    * trait is a collection of methods that types can implement
    * trait must be in scope to use its methods
    * types that implements a trait has access to the traits methods
    * given type `Type`, and trait `Trait` having method `method` then if `Type`
    implements `Trait` then we can call the method with `Type::method`
    i.e. `u64::from_str`
  * Results
    * Result value returned from a method has two variants
    `Ok(output_value)` or `Err(error_value)` or a panic
    * `.unwrap()` returns a `panic` when it receives a `None`
  * Errors
    * `writeln!` Macro writes error msg to std error output stream of `std::io::stderr()`
  * Print
    * `println!` Macro takes template string, substitutes formatted versions of arguments,
    and prints results to standard output stream
    (i.e. `println!("{:?} is {}", numbers, d);`)
  * Macros
    * macros expand to code that may use a method of a trait
  * Main Function
    * Successful program if `main` returns at all
    * Error status code upon termination by explicitly calling `expect` or `std::process::exit` 
  * Tests
    ```rust
    // marker is an attribute
    #[test]
    fn test_abc() {
      assert_eq!(abc(), 1);
    }
    ```