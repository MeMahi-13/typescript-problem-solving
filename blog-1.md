# Why `any` is a Type Safety Hole and `unknown` is the Safer Choice

## Introduction

TypeScript is popular because it helps developers catch errors before running the code. But there is one keyword that completely breaks this safety — `any`.

Many beginners use `any` to quickly fix errors, but it actually removes all the benefits of TypeScript. A safer alternative is `unknown`, which forces us to write better and more predictable code.

---

## Why `any` is Called a "Type Safety Hole"

When you use `any`, TypeScript stops checking types completely.

```ts
let value: any = "hello";
value = 42;
value.toUpperCase();