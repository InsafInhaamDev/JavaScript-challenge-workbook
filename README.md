# JavaScript challenge workbook

### **Q1. Hoisting with `var` vs `const`**

```js
// var x = undefined;

// console.log(x);

// const x = 10;

// console.log(x);
```

**Answer:**

* First `console.log(x)` → `undefined` (because `var` is hoisted & initialized as `undefined`).
* `const x = 10` → causes **SyntaxError** if both exist in the same scope.

---

### **Q2. Block Scope**

```js
var a = 5;
let b = 7;

{
    var a = 10; 
    let b = 5;  
    console.log(a + b); 
}

console.log(a + b);
```

**Answer:**

* Inside block → `10 + 5 = 15`.
* Outside block → `10 + 7 = 17` (`var` leaks outside).

---

### **Q3. Boolean + Number**

```js
console.log(true + 0);  // ?
console.log(true + 1);  // ?
console.log(false + 1); // ?
```

**Answer:**

* `true → 1`, `false → 0`.
* Output: `1, 2, 1`.

---

### **Q4. Array Addition**

```js
console.log([1, 2, 3] + [1, 2, 4]);
```

**Answer:**

* Arrays convert to strings → `"1,2,3" + "1,2,4"`
* Output: `"1,2,31,2,4"`

---

### **Q5. Loose vs Strict Equality**

```js
console.log(2 == "2");   // true
console.log(2 === "2");  // false
```

**Answer:**

* `==` does **type coercion**.
* `===` checks **value + type**.

---

### **Q6. Object Comparison**

```js
const arrA = { a: 10, b: 5 };
const arrB = { a: 10, b: 5 };

console.log(arrA == arrB);  // false
console.log(arrA.a == arrB.a);  // true
console.log(JSON.stringify(arrA) === JSON.stringify(arrB)); // true
```

**Answer:**

* Objects compare by **reference**, not value.
* Properties are equal, but object references differ.

---

# 🎯 15 More Tricky Questions

---

### **Q7. typeof null**

```js
console.log(typeof null);
```

**Answer:** `"object"` (quirk of JS since 1995).

---

### **Q8. NaN Comparison**

```js
console.log(NaN == NaN);
console.log(Number.isNaN(NaN));
```

**Answer:**

* `false` (NaN is not equal to itself).
* `true` (correct way to check).

---

### **Q9. Function Hoisting**

```js
sayHello();

function sayHello() {
  console.log("Hello!");
}
```

**Answer:** Works fine → `"Hello!"`.
(Function declarations are fully hoisted.)

---

### **Q10. Function Expression Hoisting**

```js
sayHi();

var sayHi = function() {
  console.log("Hi!");
};
```

**Answer:** `sayHi is not a function` (hoisted as `undefined`).

---

### **Q11. setTimeout Loop**

```js
for (var i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 1000);
}
```

**Answer:**
Prints `3, 3, 3` (because `var` is function-scoped).

---

### **Q12. setTimeout with let**

```js
for (let i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 1000);
}
```

**Answer:**
Prints `0, 1, 2` (because `let` is block-scoped).

---

### **Q13. Empty Array Truthy**

```js
if ([]) {
  console.log("Truthy!");
}
```

**Answer:** `"Truthy!"` → because empty arrays are objects → always truthy.

---

### **Q14. Empty Object Equality**

```js
console.log({} == {});  // false
console.log([] == []);  // false
```

**Answer:** Different references, so always `false`.

---

### **Q15. Type Coercion with +**

```js
console.log(1 + "1");   // ?
console.log("1" + 1);   // ?
console.log(1 - "1");   // ?
```

**Answer:**

* `"11"`
* `"11"`
* `0`

---

### **Q16. typeof undefined vs not defined**

```js
let x;
console.log(typeof x);    // ?
console.log(typeof y);    // ?
```

**Answer:**

* `"undefined"`
* `"undefined"` (even though `y` doesn’t exist!).

---

### **Q17. Object Keys Auto-Stringify**

```js
const obj = { 1: "a", "1": "b" };
console.log(obj[1]);
```

**Answer:** `"b"` → keys are strings internally.

---

### **Q18. Array Holes**

```js
const arr = [1, , 3];
console.log(arr.length);
console.log(arr[1]);
```

**Answer:**

* Length = `3`
* arr[1] = `undefined`

---

### **Q19. Spread Operator in Objects**

```js
const obj = { a: 1, b: 2, a: 3 };
console.log(obj);
```

**Answer:** `{ a: 3, b: 2 }` → last key overwrites.

---

### **Q20. Infinity**

```js
console.log(1 / 0);
console.log(-1 / 0);
```

**Answer:**

* `Infinity`
* `-Infinity`

---

### **Q21. parseInt Quirk**

```js
console.log(parseInt("08"));
console.log(parseInt("010"));
```

**Answer:** `8` and `10`. (Older JS treated `010` as octal in sloppy mode).

---

### **Q22. isNaN vs Number.isNaN**

```js
console.log(isNaN("hello"));       
console.log(Number.isNaN("hello"));
```

**Answer:**

* `true` (isNaN does coercion).
* `false` (Number.isNaN is strict).

---

### **Q23. String Object vs String Primitive**

```js
console.log(typeof "hello");        // string
console.log(typeof new String("hello")); // object
```

**Answer:** Primitives vs wrapper objects.

---

### **Q24. delete Operator**

```js
const obj = { a: 1 };
delete obj.a;
console.log(obj.a);
```

**Answer:** `undefined` (property removed).

---

### **Q25. Array Sort**

```js
console.log([10, 2, 30].sort());
```

**Answer:** `[10, 2, 30] → ["10","2","30"] → ["10","2","30"] → [10,30,2]`
(sort compares as **strings** by default).


---

### **Q26. Logical Operators**

```js
console.log(true || false && false);
```

**Answer:** `true` → `&&` has higher precedence than `||`.

---

### **Q27. Pre/Post Increment**

```js
let x = 5;
console.log(x++);  
console.log(++x);
```

**Answer:**

* `x++` → prints `5` (then x=6)
* `++x` → prints `7`

---

### **Q28. String + Boolean**

```js
console.log("5" + true);
console.log("5" - true);
```

**Answer:**

* `"5true"`
* `4` (`"5"` coerced to number → 5 - 1 = 4)

---

### **Q29. Nullish Coalescing**

```js
let val = null ?? "default";
console.log(val);
```

**Answer:** `"default"` → nullish coalescing only considers `null` or `undefined`.

---

### **Q30. Optional Chaining**

```js
const obj = { a: { b: 2 } };
console.log(obj?.a?.b);
console.log(obj?.x?.b);
```

**Answer:**

* `2`
* `undefined` (no error)

---

### **Q31. Function Default Parameters**

```js
function greet(name = "Guest") {
  console.log(name);
}
greet();
```

**Answer:** `"Guest"` → default parameter used.

---

### **Q32. NaN arithmetic**

```js
console.log(NaN + 1);
console.log(NaN * 2);
```

**Answer:**

* `NaN`
* `NaN`

---

### **Q33. Unary + operator**

```js
console.log(+"5");
console.log(+"hello");
```

**Answer:**

* `5` (string → number)
* `NaN`

---

### **Q34. typeof array**

```js
console.log(typeof []);
console.log(Array.isArray([]));
```

**Answer:**

* `"object"`
* `true` → use Array.isArray to detect arrays

---

### **Q35. Function returning object**

```js
function f() { return { a: 1 }; }
console.log(f());
```

**Answer:** `{ a: 1 }`

---

### **Q36. Function returning object without braces**

```js
const f = () => { a: 1 };
console.log(f());
```

**Answer:** `undefined` → arrow function with braces needs `return`.

---

### **Q37. `this` in arrow functions**

```js
const obj = {
  a: 10,
  fn: () => console.log(this.a)
};
obj.fn();
```

**Answer:** `undefined` → arrow functions do **not bind `this`**, they take from surrounding scope.

---

### **Q38. `this` in regular function**

```js
const obj = {
  a: 10,
  fn() { console.log(this.a); }
};
obj.fn();
```

**Answer:** `10` → regular function uses **calling object** as `this`.

---

### **Q39. Destructuring with defaults**

```js
const { x = 5, y = 10 } = { x: 1 };
console.log(x, y);
```

**Answer:** `1 10` → y uses default because it’s undefined.

---

### **Q40. Array destructuring**

```js
const arr = [1, 2, 3];
const [a, , c] = arr;
console.log(a, c);
```

**Answer:** `1 3` → skipped the second element.

---

### **Q41. Rest operator**

```js
const [first, ...rest] = [1, 2, 3, 4];
console.log(first, rest);
```

**Answer:** `1 [2, 3, 4]`

---

### **Q42. Spread in arrays**

```js
const arr1 = [1, 2];
const arr2 = [3, 4];
console.log([...arr1, ...arr2]);
```

**Answer:** `[1, 2, 3, 4]`

---

### **Q43. Template literals**

```js
const name = "JS";
console.log(`Hello ${name}!`);
```

**Answer:** `"Hello JS!"`

---

### **Q44. Tagged template literals**

```js
function tag(strings, val) { console.log(strings, val); }
tag`Hello ${10}`;
```

**Answer:** `["Hello ", ""] 10`

---

### **Q45. Symbol uniqueness**

```js
const s1 = Symbol("id");
const s2 = Symbol("id");
console.log(s1 === s2);
```

**Answer:** `false` → every Symbol is unique.

---

### **Q46. Object.freeze**

```js
const obj = { a: 1 };
Object.freeze(obj);
obj.a = 2;
console.log(obj.a);
```

**Answer:** `1` → cannot modify frozen objects.

---

### **Q47. `in` operator**

```js
const obj = { a: 1 };
console.log("a" in obj);
console.log("b" in obj);
```

**Answer:**

* `true`
* `false`

---

### **Q48. `instanceof`**

```js
console.log([] instanceof Array); 
console.log([] instanceof Object);
```

**Answer:**

* `true`
* `true` → arrays are also objects

---

### **Q49. Closures**

```js
function outer() {
  let count = 0;
  return () => ++count;
}
const fn = outer();
console.log(fn());
console.log(fn());
```

**Answer:**

* `1`
* `2` → closure remembers `count`.

---

### **Q50. Async with setTimeout**

```js
console.log("Start");
setTimeout(() => console.log("Middle"), 0);
console.log("End");
```

**Answer:**

```
Start
End
Middle
```

→ `setTimeout` goes to **event loop**.
