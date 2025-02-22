# CBLAS [![Package][package-img]][package-url] [![Documentation][documentation-img]][documentation-url] [![Build][build-img]][build-url]

The package provides wrappers for [CBLAS] (C).

## [Architecture]

## Example

```rust
use cblas::*;

let (m, n, k) = (2, 4, 3);
let a = vec![
    1.0, 4.0,
    2.0, 5.0,
    3.0, 6.0,
];
let b = vec![
    1.0, 5.0,  9.0,
    2.0, 6.0, 10.0,
    3.0, 7.0, 11.0,
    4.0, 8.0, 12.0,
];
let mut c = vec![
    2.0, 7.0,
    6.0, 2.0,
    0.0, 7.0,
    4.0, 2.0,
];

unsafe {
    dgemm(Layout::ColumnMajor, Transpose::None, Transpose::None,
          m, n, k, 1.0, &a, m, &b, k, 1.0, &mut c, m);
}

assert!(
    c == vec![
        40.0,  90.0,
        50.0, 100.0,
        50.0, 120.0,
        60.0, 130.0,
    ]
);
```

## Contribution

Your contribution is highly appreciated. Do not hesitate to open an issue or a
pull request. Note that any contribution submitted for inclusion in the project
will be licensed according to the terms given in [LICENSE.md](LICENSE.md).

[architecture]: https://blas-lapack-rs.github.io/architecture
[cblas]: https://en.wikipedia.org/wiki/BLAS

[build-img]: https://github.com/blas-lapack-rs/cblas/actions/workflows/build.yml/badge.svg
[build-url]: https://github.com/blas-lapack-rs/cblas/actions/workflows/build.yml
[documentation-img]: https://docs.rs/cblas/badge.svg
[documentation-url]: https://docs.rs/cblas
[package-img]: https://img.shields.io/crates/v/cblas.svg
[package-url]: https://crates.io/crates/cblas
