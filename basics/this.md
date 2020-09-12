# understanding `this` in javascript
> By default, the execution context for an execution is global — which means if a code is being executed as part of a simple function call, then `this` refers to a global object.

### `this` takes different values depending upon the usage:
1. alone
2. inside a method
3. inside a function
4. `call()`, `apply()`, `bind()`

## alone
If strict mode is enabled for any function, then the value of `this` will be marked as `undefined` as in strict mode.

## inside a method
The value of `this` refers to a newly created instance.
```js
class Person {
  constructor(fn, ln) {
    this.first_name = fn;
    this.last_name = ln;

    this.displayName = function () {
      console.log(`Name: ${this.first_name} ${this.last_name}`);
    };
  }
}

let person = new Person("Paul", "Adams");
person.displayName(); // Name: Paul Adams
```

## inside a function
```js
const car = {
  make: "Lamborghini",
  model: "Huracán",
  fullName: function () {
    console.log(this.make + " " + this.model);
  },
};
car.fullName(); // Lamborghini Huracán
```

## `call()`, `apply()`, `bind()`
If we use these method with calling function, both of these methods take as their first parameter as execution context.
  - `bind()`: allows us to set `this` value on methods
  - `call()` and `apply()`: allow us to borrow functions and set `this` value on function invocation

```js
const person = {
  firstName: "Justin",
  lastName: "Bieber",
  age: 26,
};

function setPerson() {
  return `${this.firstName} ${this.lastName}`;
}

const fullName = setPerson.bind(person);
console.log(fullName()); // Justin Bieber
```

----

### reference
- https://medium.com/better-programming/understanding-the-this-keyword-in-javascript-cb76d4c7c5e8
- https://codeburst.io/all-about-this-and-new-keywords-in-javascript-38039f71780c
