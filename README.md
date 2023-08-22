# Noir Array Helpers

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**Noir Array Helpers** is a Noir function library to manipulate arrays. This library serves a kitchen sink for various array functions the Noir community finds useful.

## Installation

In your `Nargo.toml` file, add the following dependency:

```toml
[dependencies]
array_helpers = { tag = "v0.10.0", git = "https://github.com/colinnielsen/noir-array-helpers" }
```

then `use` it in your circuits:

```rust
use dep::std;
use dep::array_helpers;

fn main(){
    let pub_key: [u8; 64] = [...];

    let (pub_key_x, pub_key_y) = split_u8_64(pub_key);
    std::println(pub_key_x);
    std::println(pub_key_y);
}
```

or

```rust
use dep::std;
use dep::array_helpers::split_u8_64;

fn main(){
let eth_addr_u8: [u8;20] = [...];

    let addr = array_helpers::u8_to_eth_address(pub_key_x, pub_key_y);
    std::println(addr);

}

```

## Usage

Here are the methods available in the library:

**NOTE**: this lib ships with constrained and unconstrained versions of each function, and are post-fixed with `_unconstrained`. (unconstrained is not currently implemented as of Noir v0.6.0, but will allow you to optimize your gate count if you do not need to constrain the computation of the function)

### `split_u8_64`

Splits an array of `u8` values, with a length of 64, into two arrays of `u8` values, each with a length of 32.

```rust
fn split_u8_64(arr: [u8; 64]) -> ([u8; 32], [u8; 32])
fn split_u8_64_unconstrained(arr: [u8; 64]) -> ([u8; 32], [u8; 32])
```

### `u8_32_to_u8_64`

Combines two arrays of `u8` values, each of length 32, into a single array of `u8` values, with a length of 64.

```rust
fn u8_32_to_u8_64(arr_a: [u8; 32], arr_b: [u8; 32]) -> [u8; 64]
fn u8_32_to_u8_64_unconstrained(arr_a: [u8; 32], arr_b: [u8; 32]) -> [u8; 64]
```

### `u8_to_u160`

Converts an array of `u8` values to a `Field` value, representing a u160 value.

**NOTE**: These are also aliased to `u8_to_eth_address`, for readability.

```rust
fn u8_to_u160(array: [u8]) -> Field
fn u8_to_u160_unconstrained(array: [u8]) -> Field

fn u8_to_eth_address(array: [u8]) -> Field
fn u8_to_eth_address_unconstrained(array: [u8]) -> Field
```

### `u8_32s_to_u64_16`

Converts two arrays of `u8` values, each of length 32, to a single array of `u64` values, with a length of 16.

```rust
fn u8_32s_to_u64_16(arr_a: [u8; 32], arr_b: [u8; 32]) -> [u64; 16]
fn u8_32s_to_u64_16_unconstrained(arr_a: [u8; 32], arr_b: [u8; 32]) -> [u64; 16]
```

### `u64_4_to_u8_32`

Converts an array of `u64` values, with a length of 4, to an array of `u8` values, with a length of 32.

```rust
fn u64_4_to_u8_32(array: [u64; 4]) -> [u8; 32]
fn u64_4_to_u8_32_unconstrained(array: [u64; 4]) -> [u8; 32]
```

## License

This project is licensed under the MIT License. See the [LICENSE](https://github.com/colinnielsen/noir-array-helpers/blob/main/LICENSE) file for details.
