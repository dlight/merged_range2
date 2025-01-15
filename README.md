Note: this crate is a fork of the original [merged_range](https://github.com/datenlord/merged_range) crate, which is not maintained anymore. More details in the issue [#1](https://github.com/dlight/merged_range2/issues/1).

# merged_range2

A crate that can merge overlapping ranges.

[![Apache licensed][apache-badge]][apache-url]
[![crates.io][crates-badge]][crate-url]
[![docs.rs][docs-badge]][docs-url]
[![CI][actions-badge]][actions-url]

[apache-badge]: https://img.shields.io/badge/license-Apache-blue.svg
[apache-url]: https://github.com/dlight/merged_range2/blob/master/LICENSE
[crates-badge]: https://img.shields.io/crates/v/merged_range2.svg
[crate-url]: https://crates.io/crates/merged_range2
[docs-badge]: https://img.shields.io/docsrs/merged_range2
[docs-url]: https://docs.rs/merged_range2
[actions-badge]: https://github.com/dlight/merged_range2/actions/workflows/ci.yml/badge.svg
[actions-url]: https://github.com/dlight/merged_range2/actions/workflows/ci.yml


## Overview

`merged_range2` is used to query whether the given range is contained in the existing range. If it is contained, return true, otherwise return false. It uses a sorted vector to store ranges, it can merge the new range with the existing ranges.

Insert and query time complexity is both O(logn).

## Example

Add the dependency to Cargo.toml

```toml
[dependencies]
merged_range2 = "1.0.0"
```

Then use it in your code

```rust
use merged_range2::MergedRange;

let mut mr = MergedRange::new();
mr.insert_range(&(1..10));
mr.insert_range(&(5..20));

assert_eq!(mr.contains_range(&(3..15)), true);
assert_eq!(mr.contains_range(&(10..21)), false);
```

## License

This project is licensed under the [Apache license][apache-url].
