# JavaScript

A minimalist's guide to modern JavaScript.



## Table of Contents

- [Structure](#structure)
- [Indentation](#indentation)
- [Semicolons](#semicolons)
- [Comments](#comments)
- [Logs](#logs)
- [Naming Conventions](#naming-conventions)
- [Variables](#variables)
- [Functions](#functions)
- [Strings](#strings)
- [Objects](#objects)
- [Arrays](#arrays)
- [Modules](#modules)
- [Conditionals](#conditionals)
- [Loops](#loops)
- [Tests](#tests)
- [Linting](#linting)



## Structure

#### Spaces or tabs

Use **spaces** and indent **2 spaces** per indentation level.


#### Line length

Keep code lines < 80 characters per line. If you're going over, that means it's time to refactor.


#### Whitespace

Maintain **3 line breaks** between blocks:

###### Bad

```javascript
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
/**
 * Does something amazing.
 */
function getSomeAmazingThings() {
  // ...
}



/**
 * This does some amazing things.
 */
function doSomeOtherAmazingThing() {
  // ...
}
```

Maintain **1 line break** between groups of statements to improve readability:

###### Bad

```javascript
function someEpicMethod() {
  let values = getSomeAmazingThings()
  // Manipulate the values
  values = values.map(doSomeOtherAmazingThing)
  values = values.map(doOneMoreOtherAmazingThing)
  return values
}
```

###### Good

```javascript
function someEpicMethod() {

  let values = getSomeAmazingThings()

  // Manipulate the values
  values = values.map(doSomeOtherAmazingThing)
  values = values.map(doOneMoreOtherAmazingThing)

  return values

}
```

Maintain **1 line break** to show a close relation to an adjacent block:

###### Bad

```jsx
/**
 * The class name.
 * @type {String}
 */
const CLASS_NAME = 'Message'

/**
 * The minimum number of characters allowed in a Message text.
 * @type {Number}
 */
const TEXT_MIN_LENGTH = 1
/**
 * The maximum number of characters allowed in a Message text.
 * @type {Number}
 */
const TEXT_MAX_LENGTH = 1000
```

###### Good

```jsx
/**
 * The class name.
 * @type {String}
 */
const CLASS_NAME = 'Message'



/**
 * The minimum number of characters allowed in a Message text.
 * @type {Number}
 */
const TEXT_MIN_LENGTH = 1

/**
 * The maximum number of characters allowed in a Message text.
 * @type {Number}
 */
const TEXT_MAX_LENGTH = 1000
```


#### Alignment

##### Variable Assignments

Align groups of variable assignments:

###### Bad

```javascript
let debug = require('debug')('javascript')
let lodash = require('lodash')
let oriento = require('oriento')

let one = 1
let fifteen = 15
let onePlusFifteen = one + fifteen
```

###### Good

```javascript
let debug   = require('debug')('javascript')
let lodash  = require('lodash')
let oriento = require('oriento')

let one            = 1
let fifteen        = 15
let onePlusFifteen = one + fifteen
```

```javascript
const debug   = require('debug')('javascript')
const lodash  = require('lodash')
const oriento = require('oriento')

const CONVERSATION = requireRoot('constants/conversation')
const MESSAGE      = requireRoot('constants/message')
const RESPONSE     = requireRoot('constants/response')
const SUBSCRIPTION = requireRoot('constants/subscription')
const TEST         = requireRoot('constants/test')
const db           = requireRoot('database')
const stripeUtil   = requireRoot('utils/stripe')
```

If the aligned variables go past the 80-character limit, don't align them:

###### Bad

```javascript
let one                                          = 'thisIsAVeryLongValueThatWillBreakTheLimit'
let two                                          = 2
let three                                        = 3
let thisIsAReallyLongVariableNameWithAShortValue = 4
```

###### Good

```javascript
let one = 'thisIsAVeryLongValueThatWillBreakTheLimit'
let two = 2
let three = 3
let thisIsAReallyLongVariableNameWithAShortValue = 4
```

##### Objects

Align values inside of objects:

###### Bad

```javascript
let object = {
  one: 1,
  two: 2,
  three: 3,
}
```

###### Good

```javascript
let object = {
  one   : 1,
  two   : 2,
  three : 3,
}
```

If one or more properties go past the 80-character limit or span multiple lines, alignment is optional:

###### Bad

```javascript
let object = {
  one                                          : 'thisIsAVeryLongValueThatWillBreakTheLimit',
  two                                          : {
    foo: 'bar',
  },
  three                                        : 3,
  thisIsAReallyLongPropertyNameWithAShortValue : 4,
}
```

###### Good

```javascript
let object = {
  one: 'thisIsAVeryLongValueThatWillBreakTheLimit',
  two: {
    foo: 'bar',
  },
  three: 3,
  thisIsAReallyLongPropertyNameWithAShortValue: 4,
}
```



## Indentation

Indent chained functions with two spaces on the following lines.

###### Good

```javascript
let response = yield request(app)
  .post(url)
  .send({})
  .expect(RESPONSE.SUCCESS.STATUS.OK)
  .end()
```

###### Bad

```javascript
let response = yield request(app)
                     .post(url)
                     .send({})
                     .expect(RESPONSE.SUCCESS.STATUS.OK)
                     .end()
```


## Semicolons

Don't use them. JavaScript has reliable ASI (automatic-semicolon-insertion) which allows for cleaner looking code.

In the few rare scenarios where a semicolon is required, JSHint will catch it. The issue should then be resolved by a small refactor or by adding a semicolon to the **front** of the line that requires it.

Example by inserting semicolon:

```javascript
function myFunc() {
  let collection = []
  ;[].map.call(arguments, function() {
    // ...
  })
}
```

Or better yet, a small refactor:

```javascript
function myFunc() {
  let collection = []
  mapArgs(arguments, function() {
    // ...
  })
}
function mapArgs(args, fn) {
  return [].map.call(args, fn)
}
```


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
* Line-specific annotations (eg. `// TODO: Change to validate once issue at http://example.com is fixed`)



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

For block comments that have 3 or fewer lines of content, do not use spacing:

```javascript
/**
 * Explains how to write a short block comment.
 * @param  {String[]} names The names of the things.
 * @return {Object[]} The names backwards because yolo.
 */
```


Here is a complete mock comment to exemplify all of the possible inclusions, as well as their **ordering** and **spacing**:

```javascript
/**
 * @deprecated because yolo
 *
 * Explains how to write an excessively long block comment.
 *
 * TODO: Make all your comments this awesome
 * FIXME: Just kidding, my code is gold
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
 *
 * @throws {Error} If the function is feeling funky.
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


## Naming Conventions

Be descriptive with your naming choice. Avoid unnecessary abbreviations because they might not be as obvious to someone else:

```javascript
// Bad
let btn  = document.getElementById('button')
let stmt = ''
let age  = user.age()

// Good
let button    = document.getElementById('button')
let statement = ''
let age       = user.getAge()
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
let MY_CONSTANT   = 500
let myVariable    = true
let myConstructor = new MyConstructor()
let myClass       = new MyClass()
let myObject      = Object.create(MyObject)
let myFunction    = function(myArg) {}
```

###### Private members

Typically, you can achieve private members through function or module scoping. However, if your class or module exposes these private members, prefix them with an underscore (`_`).

For example:

```javascript
let MyObj = function(name) {
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


## Variables

Use multiple `var` declarations instead of comma separating them:

```javascript
// Bad
let someVar      = true,
    someOtherVar = false

// Good
let someVar      = true
let someOtherVar = false
```

Use `const` if a variable is never reassigned because:
- It prevents reassignment by mistakes.
- It reduces the cognitive load for readers and reviewers.

Note:
- `const` does not protect against mutation. It only protects against reassignemnt.
- Using `const` to declare a variable does not make a constraint on future code changes. It could be changed to `let` if reassignment becomes necesary.

```javascript
// Bad
var varNeverReassigned = 'foo'

// Bad
let varNeverReassigned = 'foo'

// Good
const varNeverReassigned = 'foo'
```

If a variable is reassigned, use `let` instead. Do NOT use `var`.

```javascript
// Bad
var varReassigned = 'bar'
varReassigned = 'baz'

// Good
let varReassigned = 'bar'
varReassigned = 'baz'
```


## Functions

Know the basic terminology:

```javascript
// Anonymous function expression
let anonymous = function() {}

// Named function expression
let named = function named() {}

// Function declaration
function declaration() {}

// Arrow function
let arrow = () => {}
```

**Only use function declarations** for the sake of consistency and added benefits they come with.

```javascript
// Bad
module.exports = {
  myMethod: function() {}
}

// Bad
let myFunc = function myMethod() {}

// Bad
let myMethod = () => {}

// Good
module.exports = {
  myMethod: myMethod
}
function myMethod() {}
```

The only exception is when defining a private function within another function, you can use an **arrow function**.

```javascript
function myMethod(user) {

  let success = () => {
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
  let q = new Parse.Query(Workout)
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
let singleLine = (one) => one.map(two)

let multipleLineReturn = (options) => ({
  ...options,
  something: true,
})

let multipleLineBody = data => {
  let newData = data.map(newness)
  // ...
  return newData
}


// Good
let singleLine = one => one.map(two)

let multipleLineReturn = options => ({
  ...options,
  something: true,
})

let multipleLineBody = (data) => {
  let newData = data.map(newness)
  // ...
  return newData
}
```


###### Private functions

All private function declarations should be defined *after* the `return` statement so that the main function body is easier to digest:

```javascript
// Bad
function calculate(options) {

  let start = options.starting.map(calcStart)
  let end = options.ending.map(calcEnd)

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

  let start = options.starting.map(calcStart)
  let end = options.ending.map(calcEnd)

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
let value = getSomeValue(someObject, 'property')
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
  let x = 1
  return x + 1
}

// For functions longer than 3 lines
function myLogFn() {

  let x = 1
  let y = 2
  let z = 3

  return x * y + z

}
```

Whitespace **around function parameters** should look like this:

```javascript
// For parameters that fit a single line
let result = mySimpleFn(param1, param2, param3)

// For parameters that end with an object
let updatedSettings = reduxUtil.updateData(settings, {
  audioCues: true
})

// For parameters that don’t fit a single line
let updatedSettings = reduxUtil.updateData(
  currentUser.data.settings,
  {
    walkthrough : {
      ...currentUser.data.settings.data.walkthrough,
      overlay : {
        ...currentUser.data.settings.data.walkthrough.overlay,
        isLoaded : false,
      },
    }
  },
  { isLocal : true } // For small objects, inline is fine
)
)
```


**Note:** All of these rules are recursive, meaning if there is a function within a function, the same rules apply to that function.





## Strings

Use the literals:

```javascript
// Bad
let myString = new String()

// Good
let myString = ''
```


Use templating instead of concatenating strings:

```js
// Bad
let str = 'hey ' + user.data.name

// Good
let str = `hey ${user.data.name}`
```


Join an array of strings if they overflow:
```js
// Bad
let longString = 'hey man, i was walking down the street the other day and' +
  ' noticed a huge pile of crap on your doorstep'

// Good
let longString = [
  'hey man, i was walking down the street the other day and',
  'noticed a huge pile of crap on your doorstep',
  'so i cleaned it up',
].join(' ')
```





## Objects

Use the literals:

```javascript
// Bad
let myObject = new Object()

// Good
let myObject = {}
```

###### Trailing commas

Trailing commas are fine:

```javascript
let object = {
  prop1: true,
  prop2: false,
}
```

###### Whitespace

Whitespace around an object should look like this:

```javascript
let object = {
  prop: true,
  method: function() {}
}
```


## Arrays

Use the literals:

```javascript
// Bad
let myArray = new Array()

// Good
let myArray = []
```

Don't mess directly with the array's indices **unless** if you're mutating it with a targeted index. Use `[].push` instead.

###### Trailing commas

Trailing commas are fine:

```javascript
let array = [
  'value1',
  'value2',
]
```

###### Whitespace

Whitespace around an array should look like this:

```javascript
let shortArray = ['some', 'value', 'here']
let longArray = [
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
let isSomething = !!something
let isEmptyArray = !array.length
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
// ORs
if (
  condition1
  ||
  condition2
  ||
  condition3
) {
  // ...
}

// ANDs
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




## Tests

A good test ensures that a unit of code behaves as expected without caring about the implementation. For every test case, there should be 1 corresponding `it`. Inside of an `it`, there may be multiple tests for different examples of the test case.


###### Whitespace

There should be 3 spaces between adjacent `describe`s and 2 spaces between adjacent `it`s.

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


    it('creates a model')


    // ...


  })


})
```




## Linting

The following `.eslintrc` files are used to lint our JavaScript (based on context):


#### Frontend

```json
{
  "parser": "babel-eslint",
  "parserOptions": {
    "ecmaVersion": 6,
    "ecmaFeatures": {
      "jsx"           : true,
      "spread"        : true,
      "destructuring" : true,
    }
  },
  "extends": ["eslint:recommended", "plugin:react/recommended"],
  "rules": {
    "comma-dangle"            : [0, "always-multiline"],
    "complexity"              : [1, 6],
    "curly"                   : [2, "all"],
    "default-case"            : [2],
    "dot-notation"            : [1],
    "dot-location"            : [1, "property"],
    "eqeqeq"                  : [2, "allow-null"],
    "guard-for-in"            : [2],
    "indent"                  : [2, 2],
    "quotes"                  : [2, "single"],
    "linebreak-style"         : [2, "unix"],
    "max-depth"               : [1, 3],
    "max-len"                 : [1, 120],
    "max-params"              : [0, 4],
    "max-statements"          : [1, 20],
    "no-alert"                : [2],
    "no-caller"               : [2],
    "no-console"              : [0],
    "no-else-return"          : [1],
    "no-extend-native"        : [2],
    "no-eval"                 : [2],
    "no-floating-decimal"     : [2],
    "no-implied-eval"         : [2],
    "no-invalid-this"         : [2],
    "no-loop-func"            : [1],
    "no-multi-str"            : [2],
    "no-native-reassign"      : [2],
    "no-new-func"             : [2],
    "no-new-wrappers"         : [2],
    "no-proto"                : [2],
    "no-regex-spaces"         : 1,
    "no-return-assign"        : [2, "except-parens"],
    "no-script-url"           : [2],
    "no-self-compare"         : [2],
    "no-sequences"            : [2],
    "no-unexpected-multiline" : [2],
    "no-unused-expressions"   : [2],
    "no-unused-vars"          : [2, {"args": "none"}],
    "no-useless-call"         : [2],
    "no-var"                  : [2],
    "no-with"                 : [2],
    "radix"                   : [2],
    "react/jsx-uses-vars"     : 1,
    "semi"                    : [2, "never"],
    "valid-jsdoc": [1, {
      "prefer": {
        "returns": "return"
      },
      "requireParamDescription"  : false,
      "requireReturn"            : false,
      "requireReturnDescription" : false
    }]
  },
  "env": {
    "es6"     : true,
    "browser" : true,
    "mocha"   : true,
    "node"    : true
  },
  "ecmaFeatures": {
    "jsx"                          : true,
    "experimentalObjectRestSpread" : true
  },
  "plugins": [
    "react"
  ]
}
```


#### Backend

```json
{
  "extends": "eslint:recommended",
  "rules": {
    "comma-dangle"            : [0, "always-multiline"],
    "complexity"              : [1, 7],
    "curly"                   : [2, "all"],
    "default-case"            : [2],
    "dot-notation"            : [1],
    "dot-location"            : [1, "property"],
    "eqeqeq"                  : [2, "allow-null"],
    "generator-star-spacing"  : [2, {"before": false, "after": true}],
    "guard-for-in"            : [2],
    "indent"                  : [2, 2],
    "quotes"                  : [2, "single"],
    "linebreak-style"         : [2, "unix"],
    "max-depth"               : [1, 3],
    "max-len"                 : [1, 120],
    "max-params"              : [1, 4],
    "max-statements"          : [1, 20],
    "no-alert"                : [2],
    "no-caller"               : [2],
    "no-console"              : [0],
    "no-else-return"          : [1],
    "no-extend-native"        : [2],
    "no-eval"                 : [2],
    "no-floating-decimal"     : [2],
    "no-implied-eval"         : [2],
    "no-invalid-this"         : [2],
    "no-loop-func"            : [1],
    "no-multi-str"            : [2],
    "no-native-reassign"      : [2],
    "no-new-func"             : [2],
    "no-new-wrappers"         : [2],
    "no-proto"                : [2],
    "no-return-assign"        : [2, "except-parens"],
    "no-script-url"           : [2],
    "no-self-compare"         : [2],
    "no-sequences"            : [2],
    "no-unexpected-multiline" : [2],
    "no-unused-expressions"   : [2],
    "no-unused-vars"          : [2, {"args": "none"}],
    "no-useless-call"         : [2],
    "no-with"                 : [2],
    "radix"                   : [2],
    "semi"                    : [2, "never"],
    "valid-jsdoc": [1, {
      "prefer": {
        "returns": "return"
      },
      "requireParamDescription"  : false,
      "requireReturn"            : false,
      "requireReturnDescription" : false
    }]
  },
  "env": {
    "es6"  : true,
    "node" : true
  },
  "globals": {
    "DEBUGGING"   : true,
    "DEVELOPMENT" : true,
    "PRODUCTION"  : true,
    "readRoot"    : true,
    "REDIS"       : true,
    "requireRoot" : true,
    "STAGING"     : true,
    "TESTING"     : true,
    "UPLOAD"      : true,
  }
}
```
