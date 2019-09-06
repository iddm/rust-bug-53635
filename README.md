# [Nightly compiler bug](https://github.com/rust-lang/rust/issues/51635)

## Description

This is an MCVE for reproducing the bug when the code is not shown which
actually causes errors. The errors itselves are shown correctly. The output
looks as this:

```
Compiling bug v0.1.0 (/home/rust/src/bug)

error[E0308]: mismatched types
  | 
  = note: expected type `std::string::String`
             found type `&'static str`

error: aborting due to previous error

For more information about this error, try `rustc --explain E0308`.
error: Could not compile `bug`.

To learn more, run the command again with --verbose.
```

After bisection it was evident that the problem is seen on all nightly compilers up to these days, starting from nightly-2019-04-15. The versions before have not been tested as `serde` framework can't be compiled on earlier versions of the compiler. However, if it only had been possible to set the serde version less than `1.0.99`, we would have been able to bisect further.

More information can be found on the [bug page](https://github.com/rust-lang/rust/issues/51635).
