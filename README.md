# Late format

This crate provides a simple way of formatting parameters in a runtime string, with runtime parameter names.

This is an alternative to using complex template engines.

## Example

```rust
use hydroperx_lateformat::LateFormat;
use maplit::hashmap;

let user_string: String = "some user string: {id}".into();
assert_eq!(
    "some user string: x",
    user_string.hydroperx_lateformat(hashmap!{"id".into() => "x".into()})
);

let user_string: String = r#"some user string: {"id"}"#.into();
assert_eq!(
    "some user string: id",
    user_string.hydroperx_lateformat(hashmap!{"id".into() => "x".into()})
);

let user_string: String = r#"some user string: {  "id"  }"#.into();
assert_eq!(
    "some user string: id",
    user_string.hydroperx_lateformat(hashmap!{"id".into() => "x".into()})
);

let user_string: String = "some user string: {id}".into();
assert_eq!(
    "some user string: None",
    user_string.hydroperx_lateformat(hashmap!{})
);
```