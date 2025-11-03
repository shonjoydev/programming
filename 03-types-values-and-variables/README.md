# JavaScript Types and Variables

## Variables in JavaScript

JavaScript has three ways to declare variables:

### **var** (old way, avoid in modern code)

- Function-scoped or globally-scoped
- Can be redeclared and updated
- Hoisted to the top of their scope

```javascript
var name = 'John';
var name = 'Jane'; // OK but confusing
```

### **let** (modern, for values that change)

- Block-scoped (only exists within `{}`)
- Can be updated but not redeclared in same scope
- Not hoisted in the same way as var

```javascript
let age = 25;
age = 26; // OK
let age = 30; // Error: already declared
```

### **const** (modern, for values that don't change)

- Block-scoped
- Cannot be updated or redeclared
- Must be initialized when declared
- **Note:** Objects and arrays declared with const can still have their contents modified

```javascript
const PI = 3.14159;
PI = 3.14; // Error

const person = { name: 'Alice' };
person.name = 'Bob'; // OK - modifying object contents
person = {}; // Error - can't reassign
```

## Data Types in JavaScript

JavaScript has **8 data types**: 7 primitive types and 1 reference type (Object).

### **Primitive Types** (immutable, stored by value)

#### 1. **Number**

- Represents both integers and floating-point numbers
- Special values: `Infinity`, `-Infinity`, `NaN` (Not a Number)

```javascript
let integer = 42;
let float = 3.14;
let negative = -10;
let result = 10 / 0; // Infinity
let invalid = 'abc' / 2; // NaN
```

#### 2. **BigInt**

- For integers larger than 2^53 - 1
- Created by appending `n` to a number

```javascript
let big = 1234567890123456789012345678901234567890n;
let bigInt = BigInt(9007199254740991);
```

#### 3. **String**

- Text data enclosed in quotes (single, double, or backticks)
- Backticks allow template literals with embedded expressions

```javascript
let single = 'Hello';
let double = 'World';
let template = `Hello ${single}`; // "Hello Hello"
```

#### 4. **Boolean**

- Logical type with only two values: `true` or `false`

```javascript
let isActive = true;
let isComplete = false;
```

#### 5. **undefined**

- A variable that has been declared but not assigned a value
- Default value for uninitialized variables

```javascript
let x;
console.log(x); // undefined
```

#### 6. **null**

- Represents intentional absence of value
- Must be explicitly assigned

```javascript
let empty = null; // deliberately empty
```

#### 7. **Symbol** (ES6+)

- Unique and immutable identifier
- Often used as object property keys

```javascript
let sym1 = Symbol('description');
let sym2 = Symbol('description');
console.log(sym1 === sym2); // false - always unique
```

### **Reference Type**

#### 8. **Object**

- Collection of key-value pairs
- Includes: plain objects, arrays, functions, dates, etc.

```javascript
// Plain object
let person = {
  name: 'Alice',
  age: 30,
};

// Array
let numbers = [1, 2, 3, 4, 5];

// Function
let greet = function () {
  return 'Hello';
};

// Date
let now = new Date();
```

## Type Checking

### **typeof operator**

Returns a string indicating the type:

```javascript
typeof 42; // "number"
typeof 'hello'; // "string"
typeof true; // "boolean"
typeof undefined; // "undefined"
typeof Symbol(); // "symbol"
typeof 100n; // "bigint"
typeof {}; // "object"
typeof []; // "object" (arrays are objects!)
typeof null; // "object" (historical bug in JavaScript)
typeof function () {}; // "function"
```

### **Checking for null**

```javascript
let value = null;
if (value === null) {
  // correct way to check for null
}
```

### **Checking for arrays**

```javascript
Array.isArray([1, 2, 3]); // true
Array.isArray({}); // false
```

## Type Coercion

JavaScript automatically converts types in certain situations (implicit coercion):

```javascript
// String concatenation
'5' + 2; // "52" (number converted to string)

// Mathematical operations
'5' - 2; // 3 (string converted to number)
'5' * '2'; // 10

// Boolean context
if ('hello') {
} // non-empty string is truthy
if (0) {
} // 0 is falsy
```

### **Truthy and Falsy Values**

**Falsy values** (convert to false):

- `false`
- `0`, `-0`, `0n`
- `""` (empty string)
- `null`
- `undefined`
- `NaN`

**Everything else is truthy**, including:

- `"0"` (string with zero)
- `"false"` (string)
- `[]` (empty array)
- `{}` (empty object)
- `function(){}` (any function)

## Explicit Type Conversion

```javascript
// To String
String(123)(
  // "123"
  123
).toString(); // "123"

// To Number
Number('123'); // 123
parseInt('123px'); // 123
parseFloat('3.14') + // 3.14
  '123'; // 123 (unary plus)

// To Boolean
Boolean(1); // true
Boolean(0); // false
!!'hello'; // true (double negation)
```

## Best Practices

1. **Use `const` by default**, `let` only when you need to reassign
2. **Avoid `var`** in modern JavaScript
3. **Use strict equality** (`===`) to avoid type coercion issues
4. **Check types explicitly** when needed rather than relying on coercion
5. **Initialize variables** when you declare them
6. **Use descriptive variable names** in camelCase
7. **Be aware of falsy values** when writing conditionals

```javascript
// Good
const userName = 'Alice';
let score = 0;

// Avoid
var x = 1;
let a;
```

This covers the essentials of JavaScript types and variables! Let me know if you'd like me to dive deeper into any specific area.
