# JavaScript

A minimalist's guide to modern JavaScript.



<br />
## Table of Contents

- [Structure](#structure)
- [Semicolons](#semicolons)
- [Comments](#comments)
- [Logs](#logs)
- [Naming conventions](#naming-conventions)
- [Variables](#variables)
- [Functions](#functions)
- [Objects](#objects)
- [Arrays](#arrays)
- [Modules](#modules)
- [Conditionals](#conditionals)
- [Loops](#loops)
- [Tests](#tests)



<br />
## Structure

#### Spaces or tabs

Use **spaces** and indent **2 spaces** per indentation level.


#### Line length

Keep code lines < 80 characters per line. If you're going over, that means it's time to refactor.


#### Whitespace

Maintain at least 2 line breaks between your top-level functions and at least 1 line break between bodies of functions where it helps readability:

###### Bad

```javascript
function someEpicMethod() {
  var values = getSomeAmazingThings()
  // Manipulate the values
  values = values.map(doSomeOtherAmazingThing)
  values = values.map(doOneMoreOtherAmazingThing)
  return values
}
function getSomeAmazingThings() {
  // ...
}

/**
  This does some amazing things
 */
function doSomeOtherAmazingThing() {
  // ...
}
```

###### Good

```javascript
function someEpicMethod() {

  var values = getSomeAmazingThings()

  // Manipulate the values
  values = values.map(doSomeOtherAmazingThing)
  values = values.map(doOneMoreOtherAmazingThing)

  return values

}


function getSomeAmazingThings() {
  // ...
}


/**
 * This does some amazing things
 */
function doSomeOtherAmazingThing() {
  // ...
}
```

#### Alignment

Align groups of variable assignments:

###### Bad

```javascript
var debug = require('debug')('javascript')
var lodash = require('lodash')
var oriento = require('oriento')

var one = 1
var fifteen = 15
var onePlusFifteen = one + fifteen
```

###### Good

```javascript
var debug   = require('debug')('javascript')
var lodash  = require('lodash')
var oriento = require('oriento')

var one            = 1
var fifteen        = 15
var onePlusFifteen = one + fifteen
```


<br />
## Semicolons

Don't use them. JavaScript has reliable ASI (automatic-semicolon-insertion) which allows for cleaner looking code.

In the few rare scenarios where a semicolon is required, JSHint will catch it. The issue should then be resolved by a small refactor or by adding a semicolon to the **front** of the line that requires it.

Example by inserting semicolon:

```javascript
function myFunc() {
  var collection = []
  ;[].map.call(arguments, function() {
    // ...
  })
}
```

Or better yet, a small refactor:

```javascript
function myFunc() {
  var collection = []
  mapArgs(arguments, function() {
    // ...
  })
}
function mapArgs(args, fn) {
  return [].map.call(args, fn)
}
```


<br />
## Comments

Comments are necessary to describe to humans what a snippet of code is doing - however, they must be as concise as possible to make them easier to maintain as the snippet evolves.


### Things to do

1. Keep the present tense
  * Eg. `Will increment the follower count => Increments the follower count`
* Be concise
  * Eg.
  ```
  This function takes a variable called A and adds it to a variable called B and then returns the result. This is also called a sum. If you want to read more about sums, go back to elementary school.
  =>
  Sums A and B.
  ```
* Be explicit
  * Eg.
  ```
  Toggles button.
  =>
  Toggles the visibility of the "Start Workout" button.
  ```
* Split long lines
* Use proper spelling, punctuation, and grammar
* Group shorthand functions with the main function and only provide a single block comment
  * Eg. When defining `toggleButton(toggle)`, `showButton()`, and `hideButton()`, only provide a block comment for `toggleButton(toggle)` and put the shorthand functions immediately below it.


### Things to NOT do

1. Use pronouns (eg. we, I, you, etc.)
  - `We need this to access module X => Used to access module X`
  - `If you don't have access to X, don't call this => Requires access to X`
* Be vague
  * Eg. `This function processes data.`
* Use unnecessary punctuation
  * Eg. `Workout created!!!1`



### Types


#### Inline

Inline comments should only be inside of function bodies.

##### When to use

* Non-trivial snippets (eg. bit shifting, formulas)
* Unintuitive logic (eg. workarounds)
* Line-specific annotations (eg. `// TODO: change to validate once issue at http://example.com is fixed`)



They should always appear *before* the line they are describing:

###### Bad

```javascript
x = x + 1 // Compensate for border
```

###### Good

```javascript
// Compensate for border
x = x + 1
```


#### Block

Block comments should be made for **every function**, no matter how large or small. Use [DocBlockr](https://github.com/Warin/Sublime/tree/master/DocBlockr) to easily generate them.

For block comments that have 5 or fewer lines of content, do not use spacing:

```javascript
/**
 * Explains how to write a short block comment.
 * @param  {String[]} names        The names of the things.
 * @param  {Object}   data         The data of the things.
 * @param  {Object}   [options={}] The options you want to use.
 * @return {Object[]} The names attached to the data because yolo.
 */
```


Here is a complete mock comment to exemplify all of the possible inclusions, as well as their **ordering** and **spacing**:

```javascript
/**
 * @deprecated because yolo
 *
 * Explains how to write an excessively long block comment.
 *
 * TODO: make all your comments this awesome
 * FIXME: just kidding, my code is gold
 *
 * @private
 *
 * @example
 *   callThisFunctionWithArgs("myString", 123, {
 *     prop1: '1',
 *     prop2: '2'
 *   })
 *   // 12345
 *
 * @example
 *   callThisFunctionWithArgs("oneLiner", 1) // 12345
 *
 * @example
 *   callThisFunctionWithArgs("tooLongForOneLine", 12345, {
 *     too:   'many',
 *     props: 2,
 *     count: true
 *   }
 *   =>
 *   {
 *     it       : 'won\'t',
 *     actually : 'return',
 *     "this"   : 'because',
 *     i        : 'said',
 *     so       : '.'
 *   }
 *
 * @param {String} arg1  This is the first argument.
 * @param {Number} arg2  A number of your choice (don't pick 7).
 * @param {Object} arg3  An object.
 *        {Object} arg3.prop1 The object's property.
 *        {Object} [arg3.prop2] The object's optional property.
 * @param {Object} [obj] An optional object.
 *
 * @return {Number} Always returns 12345 because yolo.
 */
```

##### Whitespace
Leave one line break between the method's description and its parameters only if the description takes more than two lines.


#### Sectional

Sectional comments are used to organize code in modules into logical sections.
They can be easily generated using [DocBlockr](https://github.com/Warin/Sublime/tree/master/DocBlockr).
```javascript
// BEST SECTION EVER[CTRL+RETURN]
```
becomes
```javascript
///////////////////////
// BEST SECTION EVER //
///////////////////////
```

##### Whitespace
Leave five line breaks above a sectional comment and three line breaks after:
```javascript
//////////////
// SECTION1 //
//////////////



function myFunc() {
  // ...
}





//////////////
// SECTION2 //
//////////////



// ...
```


#### Module

Module comments are used to describe the contents of a module in a simple way.

```javascript
/**
 * This is the JavaScript Style Guide. You should read this
 * while drinking coffee. In here, you can find out exactly
 * what this file contains in a concise tidbit of text.
 */

// Rest of file...
```



<br />
## Logs

To aid in debugging, we add logs to our code.


### Guidelines

1. Be concise
* Avoid punctuation
* Sentence casing in *browser* and lowercase in *Node*
* Provide context
* Include variable values


### Types

Be sure to use the right type of log for your scenario:
* `console.log`    : When something happens without a user doing it
* `console.info`   : When a user does something
* `console.assert` : When an assertion needs to be made
* `console.warn`   : When something has gone wrong
* `console.error`  : When something has gone critically wrong

**Do not** use these types of logs:
* `console.debug`


### Examples

```javascript
console.log('Workout saved %o', workout)
console.info('Save workout button clicked %o', workout)
console.assert(!!workout, 'Workout does not exist')
console.warn('Workout.saveChildren is deprecated')
console.error('Tried saving workout that isn’t owned %o', workout)
```



<br />
## Naming conventions

Be descriptive with your naming choice. Avoid unnecessary abbreviations because they might not be as obvious to someone else:

```javascript
// Bad
var btn  = document.getElementById('button')
var stmt = ''
var age  = user.age()

// Good
var button    = document.getElementById('button')
var statement = ''
var age       = user.getAge()
```

If a method returns something, it should be prefixed with `get`, `is`, etc. If a method sets something, it should be prefixed with `set`, `update`, `insert`, etc.

###### Letter casings

These are the casings we use for naming things:

```
UPPER_SNAKE_CASE : used for constants
PascalCase       : used for classes
camelCase        : used for everything else
```

For example:

```javascript
var MY_CONSTANT   = 500
var myVariable    = true
var myConstructor = new MyConstructor()
var myClass       = new MyClass()
var myObject      = Object.create(MyObject)
var myFunction    = function(myArg) {}
```

###### Private members

Typically, you can achieve private members through function or module scoping. However, if your class or module exposes these private members, prefix them with an underscore (`_`).

For example:

```javascript
var MyObj = function(name) {
  this._name = name

  this.setName = function(name) {
    this._name = name
  }
  this.getName = function() {
    return this._name
  }

  return this
}
```


<br />
## Variables

Use multiple `var` declarations instead of comma separating them:

```javascript
// Bad
var someVar      = true,
    someOtherVar = false

// Good
var someVar      = true
var someOtherVar = false
```


<br />
## Functions

Know the basic terminology:

```javascript
// Anonymous function expression
var anonymous = function() {}

// Named function expression
var named = function named() {}

// Function declaration
function declaration() {}

// Arrow function
var arrow = () => {}
```

**Only use function declarations** for the sake of consistency and added benefits they come with.

```javascript
// Bad
module.exports = {
  myMethod: function() {}
}

// Bad
var myFunc = function myMethod() {}

// Bad
var myMethod = () => {}

// Good
module.exports = {
  myMethod: myMethod
}
function myMethod() {}
```

The only exception is when defining a private function within another function, you can use an **arrow function**.

```javascript
function myMethod(user) {

  var success = () => {
    console.log('Success')
  }

  user.save({ success })

}
```


##### Arguments

If there are more than 3 arguments, it is customary to use an object which contains properties that would otherwise be their own arguments.

If there are too many **required arguments**, use a `data` object.
If there are too many **optional arguments**, use an `options` object.

```javascript
function myFunc(a, b) {
  return a + b
}

function getWorkout(workoutId, options) {
  var q = new Parse.Query(Workout)
  q.get(workoutId, options)
}

function searchWorkouts(options) {
  verify(options).has({
    name: {
      type     : String,
      optional : true,
    },
    offset: {
      type    : Number,
      default : 0,
    },
  })
  ...
}

function saveDataForNextView(data) {
  console.log('Saving data for next view: %o', data)
  this._savedData = data
}
```


##### Arguments of arrow functions

The arguments of arrow functions should **always** be wrapped in parentheses, **except** when there aren't multiple lines in the body and only one argument:

```javascript
// Bad
var singleLine = (one) => one.map(two)

var multipleLineReturn = (options) => ({
  ...options,
  something: true,
})

var multipleLineBody = data => {
  var newData = data.map(newness)
  // ...
  return newData
}


// Good
var singleLine = one => one.map(two)

var multipleLineReturn = options => ({
  ...options,
  something: true,
})

var multipleLineBody = (data) => {
  var newData = data.map(newness)
  // ...
  return newData
}
```


###### Private functions

All private function declarations should be defined *after* the `return` statement so that the main function body is easier to digest:

```javascript
// Bad
function calculate(options) {

  var start = options.starting.map(calcStart)
  var end = options.ending.map(calcEnd)

  function calcStart(starting) {
    /* do some magic */
  }

  function calcEnd(ending) {
    /* do some magic */
  }

  return start.join('') + end.join('')
}

// Good
function calculate(options) {

  var start = options.starting.map(calcStart)
  var end = options.ending.map(calcEnd)

  return start.join('') + end.join('')

  function calcStart(starting) {
    /* do some magic */
  }

  function calcEnd(ending) {
    /* do some magic */
  }
}
```


###### Whitespace

Whitespace **around a function** should look like this:

```javascript
function getSomeValue(object, propertyName) {
  // ..
}
var value = getSomeValue(someObject, 'property')
```

Whitespace **around a generator** should look like this:

```javascript
// Anonymous
app.use(function* () {})

// Named
function* myGenerator() {}
```

Whitespace **within a function** should look like this:

```javascript
// For functions of 3 lines or less
function myShortFn() {
  var x = 1
  return x + 1
}

// For functions longer than 3 lines
function myLogFn() {

  var x = 1
  var y = 2
  var z = 3

  return x * y + z

}
```

Whitespace **around function parameters** should look like this:

```javascript
var results = yield db.models.Comment.getForPosts(
  [
    posts[0].id,
    posts[1].id,
  ],
  {
    userId: users[0].id,
  }
)
```


**Note:** All of these rules are recursive, meaning if there is a function within a function, the same rules apply to that function.





<br />
## Objects

Use the literals:

```javascript
// Bad
var myObject = new Object()

// Good
var myObject = {}
```

###### Trailing commas

Trailing commas are fine:

```javascript
var object = {
  prop1: true,
  prop2: false,
}
```

###### Whitespace

Whitespace around an object should look like this:

```javascript
var object = {
  prop: true,
  method: function() {}
}
```


<br />
## Arrays

Use the literals:

```javascript
// Bad
var myArray = new Array()

// Good
var myArray = []
```

Don't mess directly with the array's indices **unless** if you're mutating it with a targeted index. Use `[].push` instead.

###### Trailing commas

Trailing commas are fine:

```javascript
var array = [
  'value1',
  'value2',
]
```

###### Whitespace

Whitespace around an array should look like this:

```javascript
var shortArray = ['some', 'value', 'here']
var longArray = [
  'some',
  'values',
  'seem',
  'to',
  'go',
  'on',
  'for-',
  'wait',
  'for',
  'it',
  '-ever'
]
```


<br />
## Modules

A module's imports and exports should appear at the very top of the file:

```javascript
import 'globals'
import {sync as glob} from 'glob'

export {getFiles, setContent}
export const DEFAULT_TIMEOUT = 500

// ...rest of the file
```

A module's imports should be grouped by remote and then local, and sorted alphabetically in each group:

```javascript
let _           = require('lodash')
let Parse       = require('parse')
let React       = require('react')

let Icon        = require('components/icon/icon')
let ACTIVITY    = require('constants/activity')
let DISTANCE    = require('constants/distance')
let INTENSITY   = require('constants/intensity')
let ActivityLog = require('models/ActivityLog')
let datetime    = require('utils/datetime')
```


<br />
## Conditionals

Be explicit with your conditional checks by always using `===`, unless:

```javascript
// Checking if a value is either `null` or `undefined`
if (value == null) {}
```

Be concise with your logical checks:

```javascript
// Bad
if (something === true) {}
if (array.length === 0) {}

// Good
if (something) {}
if (!array.length) {}
```

Or better yet, cache the condition:

```javascript
// Best
var isSomething = !!something
var isEmptyArray = !array.length
if (isSomething) {}
if (isEmptyArray) {}
```

For complicated conditions, **definitely** cache the condition or even break it down into sub-conditions.

###### Whitespace

Whitespace around a conditional should look like this:

```javascript
if (isCondition) {
  // ...
}
else if (something === true) {
  // ...
}
else {
  // ...
}
```

If the function is returning between each conditional branch, remove the `else`s:

```javascript
if (isCondition) {
  return // ...
}
if (something === true) {
  return // ...
}
return // ...
```


For conditions that require more than 1 line, use the following format:

```javascript
// Only ORs
if (
  condition1 ||
  condition2 ||
  condition3
) {
  // ...
}

// Only ANDs
if (
  condition1 &&
  condition2 &&
  condition3
) {
  // ...
}

// ORs and ANDs
if (
  (
    condition1 &&
    condition2
  )
  ||
  condition3
  ||
  (
    condition4
    ||
    (
      condition5 &&
      condition6
    )
  )
) {
  // ...
}
```

Make complex conditions simpler by creating variables:
```javascript
let complexCondition = (
  condition4
  ||
  (
    condition5 &&
    condition6
  )
)

if (
  (
    condition1 &&
    condition2
  )
  ||
  condition3
  ||
  complexConditiond
) {
  // ...
}
```


<br />
## Loops

Avoid loops whenever possible. They aren't as flexible as native array methods, such as `forEach`, `map`, `filter`, etc.

When using these array methods, extract the looped function:

```javascript
// Bad
array.map(function() {})

// Good
array.map(manipulateItem)
function manipulateItem() {}
```

If you must use loops, **never** create functions within them. It's bad for performance.

###### Whitespace

Whitespace around a loop should look like this:

```javascript
for (let i = 0; i < 10; i++) {
  // ...
}
while (value === true) {
  // ...
}
do {
  // ...
} while (value === true)
```




<br />
## Tests

A good test ensures that a unit of code behaves as expected without caring about the implementation. For every test case, there should be 1 corresponding `it`. Inside of an `it`, there may be multiple tests for different examples of the test case.


###### Whitespace

There should be 3 spaces between adjacent `descibe`s and 2 spaces between adjacent `it`s.

There should be 2 spaces before nested `describe`s and 1 space before nested `it`s.

Similarly to functions, if there are more than 3 lines inside an `it`, there should be a space of padding in the function.
```jsx
describe('/WorkoutExercise', () => {


  describe('::getCalories', () => {

    it('...', () => {
      let a = 1
      let b = 2
      a.should.not.eql(b)
    })


    it('...', () => {

      let a = 1
      let b = 2
      let c = a + b

      a.should.not.eql(b)
      c.should.eql(a + b)

    })

  })



  describe('.propTypes', () => {


    describe('.range', () => {

      it('...', () => {
        // ...
      })

    })


  })


})
```


If there are **more than 10** `it`s, they must be separated by [sectional comments](#sectional).
```jsx
describe('/reduxUtil', () => {


  describe('#create', () => {


    /////////////
    // POINTER //
    /////////////


    it('creates a pointer')


    // ...


    ///////////
    // MODEL //
    ///////////


    it('creats a model')


    // ...


  })


})
```






<br><br><br><br><br><br>
