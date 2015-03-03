# mkprim 
A macro library for creating type-safe wrappers for rust's primitive types.

## Usage

To use `mkprim` in your rust program, add the following to your `Cargo.toml`:

```toml
[dependencies.mkprim]
git = "https://github.com/arbitrary-cat/mkprim.git"
```

Then, at the crate root, import it with the `macro_use` attribute:

```rust
#[macro_use]
extern crate mkprim;
```

Once you've done this, you can create primitive-like types using the `mkprim!` macro. 

```rust
mkprim! {
    Kilograms(f32);
}
```

will create a type name `Kilograms` which implements the `std::num::Float` trait.

Right now **integral types are not implemented**, but in the future you'll be able to create
newtypes based on the integer types which automatically implement `std::num::Int`.

You can specify access rights just like you would for any other newtype-style struct. So to make the
type and its implementation public, simply do:

```rust
mkprim! {
    pub Furlongs(pub f64);
}
```

You may have multiple types declared in the same `mkprim!` block:

```rust
mkprim! {
    pub Years(f32);
    pub Months(f32);
    pub Days(f32);
    pub Hours(f32);
    pub Minutes(f32);
    pub Seconds(f32);
}
```

[![Build Status](https://travis-ci.org/arbitrary-cat/mkprim.svg?branch=master)](https://travis-ci.org/arbitrary-cat/mkprim)

## Limitations

The biggest problem with `mkprim` right now is that you can't put doc comments on the types. Maybe
there's a way to make this work, but for now it causes a syntax error. Regular comments, however,
are allowed and encouraged!
