# Javascript
In Computing 2 we will be learning and using Javascript as our programming language.
Javascript is essential for building web-apps as it is the language of the web-browser.

Javascript is the world's most popular programming language (based on statistics of usage of projects on GitHub).
Part of the reason for this is that almost every computer in the world has a Javascript interpreter installed – in the form of a web-browser.
This means that code written in Javascipt can be easily run on any computer without having to install lots of additional software.

Javascript runs in Space! – on the recently launched James Webb Space Telescope and on the SpaceX Dragon 2.

Javascript's popularity is both a good and a bad thing,
since there is lots of code written in Javascript,
there is lots of *bad* code written in Javascript,
and this finds its way into some online tutorials too.
Javascript itself has matured since its introduction in 1995.
New and better features have been added to the language, but certain design mistakes and bad practices are imposible to remove without breaking large sections of the internet, so remain part of the standard.
To combat this Douglas Crockford writes about and advocates using only a subset of the language, the so-called *Good Parts*, restricting your coding to a disciplined set of best practices.
It is these *Good Parts* that we will follow in this module,
and so will be coding in a certain style and not exploring every possible aspect of the language,
but we'll find a really powerful subset that allows
us to write software that is easier to maintain and will train us to be better programmers.

As a note of clarity, Javascript is not the same language as Java – the two are quite different.
If this sounds confusing, that was indeed the original intention.
At some point in history Java looked to be the dominant language of the web, and Javascript was so named to ride that popularity.
Javascript has another name in ECMAScript, which is the standard that Javascript implements, so you may read of things such as "ES6 features", which are the new features added in the 6th edition of the ECMAScript standard, which all web-browsers now (mostly) implement.

## Language Review
In a lot of ways Javascript is very similar to Python that you have already seen.
It is a just-in-time compiled dynamically typed general purpose language.
Javascript supports multiple paradigms of coding, e.g.
imperative, object-oriented, and functional.

Following the *Good Parts*, we won't review every feature that exists in the
language, and will certainly miss out some features that will appear in code you
will find in other resources and on the internet.

We'll only consider the latest version of Javascript,
i.e. what is implemented in the current versions of mainstream web browsers and
server platforms.
If you want to support a wider base of platforms, you have to work a bit harder.

We'll refer a lot to the
[MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
here.
This is the best reference resource that exists for web technologies,
especially javascript; so you will find yourself on these pages a lot.

An alternative/supplement to this chapter is,
[A re-introduction to JavaScript (JS tutorial)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript) on MDN.
Which focuses on Javascript as a language itself,
rather than immediately embedding within a webpage.

### Variables and Values
There are a handful of built-in data types in Javascript to be familiar with.
The first set are the *primative* types:
[`boolean`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures#boolean_type),
[`number`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures#number_type),
[`string`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures#string_type), and
[`undefined`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures#undefined_type).
Next there are the *object* types:
[`array`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array),
[`object`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures#objects), and
[`function`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function)
Most of these you will have seen equivalents of in Python.
Technically there are a couple more/special cases that we won't look at here.
We'll go into more detail of what each one is below.

#### Booleans
`boolean` is a data type with two possible values `true` and `false`.
These appear everywhere and usually as answers to *yes/no* or *is* questions,
for example, if we want to determine if an array is empty, we might write,
```javascript
const array_is_empty = array.length === 0;
```
then `array_is_empty` would contain the value either `true` or `false` depending
on whether `array` was empty or not.

Booleans, or expressions that evaluate to booleans, control the flow of a program,
which code path it should take,
i.e. in `if` or `while` statements,
```javascript
if (array_is_empty) {
    // Take an action.
} else {
    // Do something else.
}
```

There's a number of logical operations –
and, or, not –
that can be performed with booleans,
```javascript
const door_secured = door_closed && door_locked; // AND &&
const problems_are_reported = !array_is_empty; // NOT !
const inspection_due = problems_are_reported || time_elapsed; // OR ||
```
These can be combined into more complicated contructions,
```javascript
const zombie_alert = (
    (zombies_outside && (inspection_due || !door_secured)) ||
    zombies_inside
);
```

Finally, a lot of values can be explicity converted to `boolean` type
using the
[`Boolean`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)
function, e.g.,
```javascript
const problems_are_reported = Boolean(problems_array.length)
```
Here if the `problems_array.length` is equal to `0`,
then `problems_are_reported` will be set to `false`,
otherwise it will be set to `true`.
`Boolean` converts *falsy* values (`0`, `undefined`, `NaN`, `""`, etc.)
to `false`, and *truthy* values (everything else) to `true`.

#### Numbers
Javascript's main numeric type is called `number`;
This is equivalent to Python's `float` type
(specifically a 64-bit IEEE 754 floating point number if you wanted to know).
Unline Python, Javascript doesn't provide a separate `int` type;
this is a *feature not a bug* since integers between
`-9007199254740991` and `9007199254740991` can be represented exactly
as a `number`.
This means the following are all `number`s:
```javascript
const lucky_number = 7;
const half = 0.5;
const minus_pi = -3.141592653589793;
let days_since_last_accident = 0;
```

Numbers have a set of arithmetic operators available to them,
these return other numbers as you would expect.
```javascript
const addition = 6 + 4; // 10
const subtraction = 6 - 4; // 2
const multiplication = 6 * 4; // 24
const division = 6 / 4; // 1.5
const remainder = 6 % 4; // 2
const exponentiation = 6 ** 4; // 1296
```
There are also relational operators,
`<`, `<=`, `>`, `>=`, `===`, `!==`,
which are
*less than*, *less or equal to*, *greater than*, *greater or equal to*,
*equal to*, *not equal to*,
resectively.
These combine two `number`s and return a `boolean`,
```javascript
5 < 3 // false
```

Like with booleans, there is a function
[`Number`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)
that will convert
from other data types into a number,
```javascript
Number("300") // 300
```
This object itself has a number of properties and methods,
E.g.
```javascript
Number.isInteger(1.5) // false
Number.EPSILON // 2.220446049250313e-16
```
Though the most useful properties and methods are found on the
[`Math`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math)
object.
This is built in and doesn't need to be imported.
```javascript
Math.PI // 3.141592653589793
Math.log(2) // 0.6931471805599453
Math.floor(5.32) // 5
```
It contains the elementary functions you would expect to see,
and mathematical constants like *π* and *e*.

#### Strings
Javascript's text type is called `string`,
which is short for string of characters.
It holds textual data e.g.,
```javascript
"Keep door closed at all times"
"w"
"🧟🧟🧟"
```
Javascript does not make a destinction between a single character and a string,
but you can extract individual characters from strings,
```javascript
"The forty-fifth character of this string is: p"[45] // "p"
```
Strings themselves have a number of
[useful methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String).
```javascript
const report = "19:45 - Zombie alarm triggered. Pizza delivery driver had been misidentified."

report.includes("zombie") // false
report.toUpperCase()
    // "19:45 - ZOMBIE ALARM TRIGGERED. PIZZA DELIVERY DRIVER HAD BEEN MISIDENTIFIED."
report.toUpperCase().includes("ZOMBIE") // true
```

Strings can be combined with the `+` operator, this is called concatenation.
```javascript
let days_since_last_incident = 0
"Notice: " + days_since_last_incident + " Days since last incident"
    // "Notice: 0 Days since last incident"
```
However this can produce code that is a little unwieldy.
An alternative to combining strings is with *template literals*,
these are strings that are delimited by the *backtick* character, `` ` ``,
(Found to the left of `1` on many keyboards)
and allow expressions to be embedded within, e.g.,
```javascript
let days_since_last_incident = 0
`Notice: ${days_since_last_incident} Days since last incident`
    // "Notice: 0 Days since last incident"
```

#### Undefined
The last primitive type to discuss is `undefined`.
This is javascript's bottom value.
It is the value returned when a declared variable has not been initialised,
or the returned value of a function that doesn't explicitly return anything.

Where the `boolean` type has two values `true` and `false`,
the `undefined` type has only one value: `undefined`.

```javascript
let counter;
counter // undefined

console.log("hello") === undefined // true
/* console.log will print a value to the console as it's action, but will return undefined. */
```

Javascript also has `null` as a bottom value.
Languages should have at most one bottom value,
and Javascript itself uses `undefined` internally in almost all cases.
When we need to, we shall too – and not use `null`.
The exception is when declaring empty objects,
which we will cover separately below.

#### Arrays
We have just looked at the primative types: `boolean`, `number`, `string`, and
`undefined`.
These are simple types that aren't made up of anything else.
The next set we will look at is the *object* types, these are compound types
because they are made up of other types.

The first object type is the `array`.
This is an ordered list of values, of any type.
In python, this is equivalent to the `list`,
there isn't a separate `tuple` type in Javascript.

```javascript
const my_array_of_numbers = [1, 2, 5, 7];
const mixed_array = ["Bill", 67];
```
Entries in the array are indexed numerically, starting at zero.
```javascript
my_array_of_numbers[3] // 7
mixed_array[0] // "Bill"
```
They each have a length property giving you the number of elements,
```javascript
my_array_of_numbers.length // 4
mixed_array.length // 2
```

You can nest any type of value in an array,
allowing you to make more complex data structures,
```javascript
const grid = [
    ["X", "O", " "],
    [" ", "X", " "],
    ["O", "X", "O"]
];

grid[0][1] // "O"

const daily_durations_of_breaches = [
    [10.23, 4.33, 9.01],
    [],
    [21.22],
    [1.45, 30.23]
]
```
We represent the empty array as `[]`.

Unlike primitive values, whose values are fixed,
object types such as arrays can be modified,
```javascript
const array = [3, 5, 9];
array[1] = 6;
array // [3, 6, 9]
```
Though we'll be looking at a coding style that avoids mutating objects.

Every array has a
[set of methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)
attached to them, and some of these are incredibly useful!
```javascript
const lunch_ingredients = ["eggs", "beans", "chips", "mushrooms"]
lunch_ingredients.includes("mushrooms") // true

const weekly_durations_of_breaches = daily_durations_of_breaches.flat() // [10.23, 4.33, 9.01, 21.22, 1.45, 30.23]
```
Some of these methods return other data types,
some return new arrays, and some mutate the original array,
unfortunately some mutate the origninal array when they could have returned a new one.
```javascript
const forward = [2, 4, 6, 8, 10];
const backward = forward.reverse();
backward // [10, 8, 6, 4, 2]
forward // [10, 8, 6, 4, 2]
```
For this reason, outside of this Javasript language review, we'll look into
using a library of utility functions that keeps the original array unchanged.

Some of the most useful array methods are `map`, `filter`, `reduce`.
These each take a `function` as an argument, and we'll look at these
when we cover functions.

#### Objects
The next object type is the `object`.
In other languages, like Python, this one might be called Dictionary.
These are key-value pairs, similar to arrays, but indexed with `strings`
instead of numbers.
```javascript
const employee = {
    "name": "Bill",
    "age": 67,
    "position": "Janitor",
    "awards": [
        "Employee of the Month – April",
        "Best Halloween Costume"
    ],
    "inventory": {"left_hand": "torch", "right_hand": "spanner"}
};
employee.name // "Bill"
employee.inventory.right_hand // "spanner"
employee["age"] // 67
```
Above, we've accessed a variable using dot notation `employee.name`
as well as subscript notation `employee["age"]`.
Like arrays, these can be nested as too, and contain any value within,
including other objects and arrays.

The empty object is specified with the object literal `{}`.

#### Functions
One of the most powerful features of Javascript is its functions.
As you have seen in other languages, structuring your programs in functions
allow for re-use of a piece of logic multiple times,
generalisation of a problem with arguments to the function,
and separation of logic to better structure your programs.

There are a few ways to declare functions in Javascript,
I'll showcase only two here, the first is the function expression,
```javascript
const double = function (x) {
    return 2 * x;
};
```
Here we have a function called `double`,
that we can pass an argument `x` to
and it will return the value `2 * x` when it is called.
```javascript
double(5.3) // 10.6
```
Functions can be more complicated than that,
and can have any number of statements within them.
```javascript
const write_invitation = function (invitee, day) {
    const salutation = `Hello ${invitee}!`
    if (day === "Saturday") {
        return `${salutation} please come to my party at the park on Saturday`.
    }
    return `${salutation} you are invited to drinks at The Rooftop on ${day}`;
};
```
In this case there were multiple return statements too,
```javascript
write_invitation("Jim", "Saturday")
    // "Hello Jim! please come to my party at the park on Saturday"
write_invitation("Sue", "Friday")
    // "Hello Sue! you are invited to drinks at The Rooftop on Friday"
```

What makes functions stand out in Javascript is that they are are an object-type
value. This means you can store a function in a variable,
put one in an array or an object, pass them to and return them from a function.
```javascript
const numerical_derivative = function (f, x) {
    const dx = 1e-8;
    return (f(x + dx) - f(x)) / dx;
};

const parabola = function (x) {
    return x ** 2;
};

numerical_derivative(parabola, 1) // 1.999999987845058
```
In the function above we are passing the function `parabola`,
which is the *y* = *x*² function, as an argument to
`numerical_derivative`, which will approximate the derivative
using a forward-difference rise over run.
i.e. d*y*/d*x* at *x* = 1.
We get a value very close to `2`, as we would expect with some numerical error.
Note how we've just passed `parabola` as if it was any other value.

If a function just returns a single expression,
we can shorthand this using the arrow notation,
```javascript
const parabola = (x) => x ** 2;
```
This behaves in the same way as the definiation above.
but can be easier to read once you've got your head around the new format.

Do note there is no return statement here,
the result of the statement will be automatically returned.

We'll go deeper into the weeds later, but you will even see this format for a function that returns a function,
```javascript
const multuply_by = (x) => (y) => x * y;
const double = multiply_by(2);
double(7) // 14
```
This is equivalent to the following in long form,
```javascript
const multuply_by = function (x) {
    return function (y) {
        return x * y;
    };
};
const double = multuply_by(2);
double(7) // 14
```

#### Variables
So far we have been talking about *values*,
We've used but, not explicitly discussed *variables*.

One mental model is that a variable is a box that holds
a value.
As such, the variables themselves don't have a type,
but the value that is in the box has a type, e.g. one of the types discussed above.

A different mental model, is that the variable isn't a box that stores a value, but is an arrow that points to a variable.
This is slightly more versatile, and closer to the truth, but a little more abstract.

There are two main ways to declare a variable in Javascript.
Using the keywords `const` and `let`.
(There is a third too `var`, but this is older and we'll never use it.)

```javascript
const my_number = 2;
let counter = 0;
let will_define_later;

will_define_later // undefined
counter = counter + 1;
counter // 2
will_define_later = "Now is the time";
will_define_later // "Now is the time"
my_number // 2
my_number = 8; // Uncaught TypeError: Assignment to constant variable.
```
Variables declared with `const` will never change their value once assigned, and need to be assigned immediately on declaration.
Whereas variables declared with `let` can be modified, and can even declared without an initial value. (They will hold `undefined` until changed.)

You may think that `let` sounds the better option because it's more
flexible, but this can lead you astray.
**Always use `const` unless you *absolutely need* to use `let`'s features.**
The advantage of `const` is that once defined it's value *never* changes.
This is a good thing, as it gives us confidence in our code, and aids
understandability.
A good source of bugs is a variable holding a different value than the one you expected it to hold.

Similar to variable declarations are object properties.
The properties of an object act as variables, in that they are a box to store other values (or technically to point to other values).
```javascript
const status_report = {};
status_report.days_since_last_accident = 0;
status_report.days_since_last_accident += 1;
status_report.days_since_last_accident // 1;
```
Here the object is `status_report`, and we've added a property
`days_since_last_accident` to it.
You'll notice that even though the *object* `status_report` is
declared as constant, we can still change it's properties.
No rules have broken here.
We are unable to change `status_report` to another value,
but we are able to *mutate* the properties of the value that is
already there.

We can lock this down if needed using `Object.freeze`, e.g.,
```javascript
const week_review = {};
week_review.accidents_this_week = 2;
Object.freeze(week_review);
week_review.accidents_this_week = 3; // This line will silently do nothing.
week_review.accidents_this_week // 2
```

Function parameters are similar to variables, e.g.,
```javascript
const make_louder = function (quiet_string) {
    const string_in_caps = quiet_string.toUpperCase();
    return `${string_in_caps}!!!`;
};
make_louder("hello") // "HELLO!!!"
```
Here `quiet_string` is a parameter to the function,
it acts as if it was a `let` variable in the function body.

#### Scope

One of the most important things to understand about variables is their *scope*.
That is, where in the rest of the code the variable can be seen.

Javascript has function scope, which means that variables declared
in a function are not accessible outside each invocation of the function.

Let's look at the previous example,
```javascript
const make_louder = function (quiet_string) {
    const string_in_caps = quiet_string.toUpperCase();
    return `${string_in_caps}!!!`;
};
make_louder("hello") // "HELLO!!!"
make_louder("Don't panic") // "DON'T PANIC!!!"
string_in_caps // Uncaught ReferenceError: string_in_caps is not defined
```

See how the `const` variable `string_in_caps` inside `make_louder`
will take the value `"HELLO"` on the first invocation of the function,
and `"DON'T PANIC"` on the second.
The variable only exists for each function invocation,
so each time the function is called `string_in_caps` is a different
variable, and gets assigned a different value.
Again no rules are broken here, you cannot change the value of `make_louder` *within* the function after assingment.
Note that outside the function `string_in_caps` is unavailable.

Variables that are defined outside a function body will be in scope within that function,
if they were in scope when the function was declared.
That's a complicated sentence, so let's look at an example.

```javascript
const factor = 3;
const triple = function (number_to_triple) {
    return factor * number_to_triple;
};
```
Here `factor` was defined outside the function `triple`,
but it is within scope of the function.

A more advanced aspect of scope is
[*closure*](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures),
Which is a powerful feature that we'll discuss this in this module,
but it's a more technical than this introductory review needs.

Finally, Javascript has *module scope* which means variables declared in one module file will not be visible outside the file unless explicitly exported.
Again this is a good thing, since you can be confident that code from elsewhere isn't influencing the code you're working on, which can lead to bugs.

### Control Flow
I've mainly talked about values, types, and variables here,
but a language will allow for control flow and branching.
I.e. when to change behaviour with an `if` statement, when to loop etc.

MDN will cover the full details of the language in
* [Control flow and error handling](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)
* [Loops and iteration](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Loops_and_iteration)

But in it's completeness, doesn't always focus on best practice.

The most important statements are,
* `if` and `else`
* `while`

The following trio are used for error handling,
* `try`, `catch`, `finally`

Useful operators are
* Logical *AND* `&&`, Logical *OR* `||`
* Ternary operator `? :`

I don't use the `for` statement or variants as the
[array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)
methods
[`.map`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
and
[`.forEach`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)
are better in almost all cases and less prone to scope bugs.

[JSLint](https://www.jslint.com/help.html),
which is a code quality tool, has opinions on which ones
should and shouldn't be used,
and what formatting allows you to write code that is less prone to bugs.
It is based on Douglas Crockford's
[*The Good Parts*](https://library-search.imperial.ac.uk/permalink/44IMP_INST/f7tnsv/alma9955838425801591).
It is very strict, but I find my programs and my coding is much improved by following rigidly.

## JSON
A discovery made about Javascript,
is that it's syntax for object expressions is a good cross-language
specification for data exchange,
since almost all languages have some form of key-value pair dictionary (`object` is Javascript) and some ordered list (`array` in Javascript).

[JSON](https://www.json.org/json-en.html),
**J**ava**S**cript **O**bject **N**otation is this standard.

It's uses include transferring data between web-server and web-browsers,
between servers, and for configuration files, as we'll see in VSCode.

It looks familiar,
```json
{
  "name": "zombie-siege",
  "type": "module",
  "version": "1.0.0",
  "description": "",
  "main": "web-app/server/server.js",
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "docdash": "^1.2.0",
    "mocha": "^9.2.2"
  },
  "dependencies": {
    "express": "^4.17.3"
  }
}
```
This is the `package.json` file of my
[Zombie Seige](https://github.com/fourier-space/zombie-siege) Repository.

The differences from Javascript are,
It's a data expression only, no statements, operators, or functions.
`undefined` is not used `null` is instead.
But for nested objects and arrays, with strings, number, and boolean values, it's quite versitile and useful.

## Closing Remarks
This has been a quick review of Javascript
for those familiar with coding, i.e. in Python.
There are more features in the language that is neccesary to use in your code,
and indeed some features to be actively avoided.
This document doens't go into the full depth of javascript but
is a reference to make you more familiar and avoid some of the key pitfalls of code you'll see in the wild.
