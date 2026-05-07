# How Generics Make TypeScript Code Reusable and Type-Safe

## Introduction

When building applications, we often write similar logic for different types of data like strings, numbers, or objects. Writing separate functions for each type can make the code repetitive and harder to manage.

This is where Generics in TypeScript become very useful. Generics allow us to write one flexible function that works with different types while still keeping type safety. In this blog, we will explore how generics help us write clean, reusable, and reliable code.

## Problem Without Generics

Without generics, we may end up writing duplicate functions like this:

```ts
function getString(value: string): string {
  return value;
}

function getNumber(value: number): number {
  return value;
}
````
Here, the logic is the same, but we are repeating code for different types.

## Solution Using Generics

Generics allow us to write a single function that works with any type.

```ts id="sk9e4u"
function getValue<T>(value: T): T {
  return value;
}
```

Now this function can be used with different types:

```ts id="v86k2x"
getValue<string>("hello");
getValue<number>(42);
getValue<boolean>(true);
```

This makes the code more flexible and reusable.

## Generics with Objects

Generics are even more powerful when working with objects.

```ts id="d2s4q9"
function getProperty<T, K extends keyof T>(obj: T, key: K): T[K] {
  return obj[key];
}
```

In this example:

* `T` represents the object type
* `K` ensures the key exists in the object
* The return type is automatically correct

## Conclusion

Generics are one of the most powerful features of TypeScript. They allow developers to write flexible and reusable functions without losing type safety.