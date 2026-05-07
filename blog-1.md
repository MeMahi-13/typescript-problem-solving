
# Why `any` is a Type Safety Hole and `unknown` is a Safer Choice

## Introduction

TypeScript is used to make JavaScript safer by checking types before running the code. But there is one keyword that breaks this safety — `any`.

Many developers use `any` to avoid errors quickly, but it can create bigger problems later. A better and safer option is `unknown`.

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

This is why `any` is called a "type safety hole" — it removes all protection.

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
* We cannot use the value directly without validation

This helps prevent runtime errors.

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

