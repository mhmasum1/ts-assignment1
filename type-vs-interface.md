# Type vs Interface in TypeScript

## Introduction

When I started learning TypeScript, I was confused about `type` and `interface`. Both can describe the shape of an object, so which one should I use? In this blog, I will explain the main differences in a simple way.

## Main Differences

An interface is mostly used to describe objects. A type alias is more flexible because it can name any type, like a union or a tuple.

```ts
interface User {
  name: string;
}

type Status = "active" | "inactive";
```

Interfaces can be extended using `extends`, and they can also be merged. If you write the same interface name twice, TypeScript combines them into one. A type alias cannot do this, and it will show an error.

```ts
interface Car {
  brand: string;
}
interface Car {
  year: number;
}
```

Type aliases use `&` to combine types instead.

```ts
type Admin = User & { role: string };
```

Interfaces are also a good choice for classes, because a class can use `implements` with them.

## When to Choose One

Use `interface` for objects and classes. Use `type` for unions, tuples and other special types.

## Conclusion

For simple objects, both are very similar. A good rule for beginners is to use `interface` for object shapes and `type` for everything else. Most importantly, choose one style and stay consistent in your project.
