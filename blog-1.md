
# Why `any` is a Type Safety Hole and `unknown` is a Safer Choice

## Introduction

One of the main reasons developers use TypeScript is to catch errors before the code runs. It helps us write safer and more reliable programs by enforcing types.

However, there is one keyword that completely removes this safety which is `any`. While it may seem convenient at first, using `any` can lead to unexpected bugs and runtime errors. A better alternative is `unknown`, which still allows flexibility but forces us to handle data more carefully. In this blog, we will understand why `any` is risky, why `unknown` is safer, and how type narrowing helps us write better code.


## Why `any` is Called a "Type Safety Hole"

When we use `any`, TypeScript stops checking the type completely.

```ts
let value: any = "hello";
value = 10;
value.toUpperCase();
````

In this example:

* TypeScript does not show any error
* But at runtime, the code will crash because numbers do not have `toUpperCase()`

This is why `any` is called a "type safety hole" .It removes all protection.

## Why `unknown` is Safer

The `unknown` type is similar to `any`, but much safer.

```ts
let value: unknown = "hello";

if (typeof value === "string") {
  value.toUpperCase();
}
```

Here:

* TypeScript forces us to check the type first
* We cannot use the value directly without validation. This helps prevent runtime errors.

## What is Type Narrowing?

Type narrowing means checking a value’s type and making it more specific before using it.

```ts
function handleValue(value: unknown) {
  if (typeof value === "string") {
    return value.toUpperCase();
  }

  if (typeof value === "number") {
    return value.toFixed(2);
  }

  return "Invalid value";
}
```

In this example:

* We check the type using `typeof`
* TypeScript understands the correct type inside each block

This makes the code safe and predictable.

## Conclusion

* `any` removes type safety and should be avoided
* `unknown` is safer because it forces type checking
* Type narrowing helps us safely work with unknown data

