# what's the differences between `var`, `let`, and `const`?

**[ECMAScript](https://en.wikipedia.org/wiki/ECMAScript#:~:text=ECMAScript%20(or%20ES)%20is%20a,pages%20across%20different%20Web%20browsers.)** (ES) is the base language of JavaScript. 
Before, there is only one way to define variables by using `var`. 

In ES8 (ECMAScript2017), `let` and `const` were born. So, what's the different?

### `var`
- redefinable
- function-scope
- weaknesses: you might _not_ realize that a `var` has already been defined before. it could be redefined.

### `let`
- same as `var`, `let` is also redefinable
- block-scope

### `const`
- constant
- block-scope

### hoisting
- `var` is hoisted at the top and initialized with undefined
- `let` and `const` are also hoisted but must be initialized

### example
- `let` implementation
```js
for (let i = 0; i < 3; i++) {
  console.log(i);
}

console.log(i);
// 0
// 1
// 2
// ReferenceError: i is not defined
```

- `var` implementation
```js
for (var i = 0; i < 3; i++) {
  console.log(i);
}

console.log(i);
// 0
// 1
// 2
// 3 => the value of i outside for-loop
```

---
### references
- https://alligator.io/js/var-let-const/
- https://github.com/lukehoban/es6features
