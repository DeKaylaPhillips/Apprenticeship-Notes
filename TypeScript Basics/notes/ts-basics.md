# TYPESCRIPT BASICS

**What is JavaScript?**

- ECMAScript
- used to create interactive web browser experiences
- has optimized execution engines (dynamic compilations)
- has extended its functionalities (adding APIs)
- can be used outside the context of a browser (such as implementing JS servers using node.js)
- good for cross-platform development
- designed for quick uses, and has grown to be a tool useful for writing applications

**TypeScript - A Static Type Checker:**

- *Static Checking*: to detect errors in code without running it
- *Static Type Checking*: to determine what is an error and what is not an error based on the values being operated on

- TS checks a program for errors BEFORE execution
    --> static checking

- TS checks a program BASED the kinds of values being returned
    --> static type checking

- Thus, TS is a *static type checker*.

**JavaScript Quirks vs. TypeScript Errors:**

```javascript
// javascript 

if ("" == 0) {
    // It is! But why??
};

const obj = { width: 10, height: 15 };
// Why is this NaN? Spelling is hard!
const area = obj.width * obj.heigth;

console.log(4 / []);
// Logs Infinity...
```

```typescript
// typescript

const obj = { width: 10, height: 15 };
const area = obj.width * obj.heigth;
// Error: Property 'heigth' does not exist on type '{ width: number; height: number; }'. Did you mean 'height'?

console.log(4 / []);
// Error: The right-hand side of an arithmetic operation must be of type 'any', 'number', 'bigint' or an enum type.
```

About TypeScript:

*Syntax:*

- superset of JS
- JS syntax = legal TS

*Types:*

- typed superset
- adds rules about how different kinds of values can be used

*Runtime Behavior:*

- TS preserves the runtime behavior of JS

*Erased Types:*

- TypeScript compiler checks the code
- TypeScript erases the types to produce the resulting "compiled" Javascript code
- TypeScript has no additional TypeScript-specific framework to learn

*Types by Inference:*

```typescript
let helloWorld = "Hello World";
let helloWorld: string;
```

*Utility Types:*

- facilitate common type transformations

`Awaited<Type>`

- models operations like `await` in `async` functions, or the `.then()` method on `Promises`

```typescript
type A = Awaited<Promise<string>>;

type A = string

type B = Awaited<Promise<number>>;

type B = number

type C = Awaited <boolean | Promise<number>>;

type C = number | boolean
```

`Partial<Type>`

- constructs a type with all properties of `Type` set to optional

```typescript
interface ToDo {
    title: string;
    description: string;
}

function updateToDo(todo: ToDo, fieldsToUpdate: Partial<ToDo>) {
    return { ...todo, ...fieldsToUpdate };
}

const todo1 = {
    title: "organize desk",
    description: "clear clutter",
};

const todo2 = updateToDo(todo1, {
    description: "throw out trash",
});
```

**CLASSES:**

Creating a class instance

```typescript
class ABC { ... }
const abc = new ABC()
```

**private x vs. #private:**

- prefix private is a *type-only addition*, and has *no effect* at runtime
- *code outside of the class can reach into the item* in the following case...

```typescript
class Bag {
    private item: any
}
```

- runtime #private has enforcement inside the JavaScript engine 
- it is only accessible inside the class

```typescript
class Bag {
    #item: any
}
```
