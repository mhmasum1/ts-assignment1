# Combining Union and Intersection Types in TypeScript

## Introduction

Union (`|`) and intersection (`&`) types look small, but they are very useful. A union means "this OR that". An intersection means "this AND that". In this blog, I will use both in one simple example.

## Practical Example

Imagine an app that returns two kinds of results: a success or an error. First, I create a union type for the result.

```ts
type Success = { status: "success"; data: string };
type Failure = { status: "error"; message: string };

type ApiResult = Success | Failure;
```

A value of `ApiResult` can be either `Success` or `Failure`. To use it safely, I check the `status` field.

```ts
function showResult(result: ApiResult): string {
  if (result.status === "success") {
    return result.data;
  }
  return result.message;
}
```

Now I want every result to also have a timestamp. I can use an intersection to add extra properties.

```ts
type WithTime = { time: number };
type TimedResult = ApiResult & WithTime;
```

Now `TimedResult` must have the `time` property, and it must also be either a success or an error.

## Conclusion

Use a union when a value can be one of many types. Use an intersection when you want to join types together. When you combine both, you get code that is flexible and safe.
