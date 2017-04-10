# Testing JavaScript

1. [Writing Tests](#writing-tests)
* [Concepts](#concepts)
* [Libraries](#libraries)



<br />

## Writing Tests


### Describing Modules and Units

When describing a **directory** or **module**, use a leading slash (`/`):
```jsx
describe('/components', () => {
  require('./components/index.tests')
})
```

When describing a **component**, use the JSX notation:
```jsx
describe('<Modal />', () => {
  // ...
})
```

When describing a **static method**, use a leading hash (`#`):
```jsx
describe('/Dom', () => {
  describe('#show', () => {
    // ...
  })
})
```

When describing an **instance method**, use double leading colons (`::`):
```jsx
describe('/WorkoutExercise', () => {
  describe('::getCalories', () => {
    // ...
  })
})
```

When describing a **static property**, use a leading period (`.`):
```jsx
describe('/Comment', () => {
  describe('.MAX_LENGTH', () => {
    // ...
  })
})
```

When describing an **instance property**, use double leading periods (`..`):
```jsx
describe('<Modal />', () => {
  describe('..props', () => {
    describe('.theme', () => {
      // ...
    })
  })
})
```


<br />


### Defining Unit Functionality

Tests should always begin with the action e.g `returns`, `gets`, `saves`, `throws` etc.

```jsx
it('returns a string with the mentions wrapped in anchor tags', ...)
```


<br />


### Making Assertions

```jsx
fn.callCount.should.eql(1)
fn.lastCall.args.length.should.eql(3)
```


<br />


### Testing Error Handling


When testing that an error is thrown, use `co` to wrap the bound function, and get a promise.
Ensure the promise gets rejected by chaining `should.be.rejected()` or `should.be.rejectedWith()`

Note: Avoid using `yield co(...).should.eventually.throw()` since it would not work if tested function is promisified.
The error is thrown in the context of a callback, and not caught by should.js, which wraps the promise.
At the same time promise rejection is not handled with this syntax.
Example:
```js
it('ensure an error is thrown', function* () {

  let gen_throw = function* (arg1) {
    throw Error(arg1)
  }
  let fn_reject = function(arg1) {
    return Promise.reject(Error(arg1))
  }
  let fn_throw = function(arg1) {
    throw Error(arg1)
  }

  // For synchronous functions just use `fn.should.throw()`.
  // Bind arguments if needed.
  fn_throw.bind(null, 'abc').should.throw('abc')

  // Using `co(...).should.be.rejected()` ensures consistent behavior with all types of inputs
  yield co(gen_throw('abc')).should.be.rejectedWith('abc')
  yield co(fn_reject('abc')).should.be.rejectedWith('abc')
  yield co(fn_throw('abc')).should.be.rejectedWith('abc')

  // Avoid `co(...).should.eventually.throw()`
  yield co(fn_reject('abc')).should.eventually.throw('abc')
  // Will throw an un-handled promise rejection or give a warning
  // Will not ensure 'abc' == 'abc'

})


it('requires a valid session token', function* () {

  let ctx = belinda.createCtx(null, {
    method       : REQUEST.METHOD.POST,
    path         : router.url('post', { className: 'Post' }),
    sessionToken : 'invalid',
  })
  let next = function* () {}

  yield co(
    setSessionUser.call(ctx, next)
  )
  .should.be.rejectedWith({
    status  : RESPONSE.ERROR.STATUS.BAD_REQUEST,
    message : RESPONSE.ERROR.MESSAGE.API.INVALID_SESSION_TOKEN
  })

})
```


### Known Issues

`should#assertion` gives wrong error messages when assertions fail for sequelize objects (or their collections).

```js
let users = yield belinda.create('User', 5)

users.should.have.size(5)
// No error

users.should.have.size(2)
// `TypeError: this.getHashtags is not a function`

users.length.should.eql(2)
// `AssertionError: expected 5 to equal 2`
```





###### [More about assertions](http://shouldjs.github.io/)



<br />

## Concepts


### Stubs

Functions that record and report on how they’re being called.

A stub can be:

1. Anonymous: `sinon.stub()`
* An object’s method: `sinon.stub(obj, 'methodName')`
* An object’s method replaced: `sinon.stub(obj, 'methodName', function replacedValue() {})`


#### Example

```jsx
// Create the stub
let showStub = sinon.stub(DomHelper, 'show')

// Invoke the unit being tested which internally calls `DomHelper.show(node, callback)`
MyModuleBeingTested.unitBeingTested(node, callback)

// Ensure the stub was called as expected
showStub.callCount.should.eql(1)
showStub.lastCall.args.length.should.eql(1)
showStub.lastCall.args[0].should.be.exactly(node)
showStub.lastCall.args[1].should.be.exactly(callback)

// Restore the stub back to normal
showStub.restore()
```


<br />

###### [More about stubs](http://sinonjs.org/releases/v2.1.0/stubs/)



<br />

### Spies

Functions that record and report on how they’re being called.

The main difference between spies and stubs is that spies actually invoke the wrapped method as it were normally called.

A spy can be:

1. Anonymous: `sinon.spy()`
* A method: `sinon.spy(function method() {})`
* An object’s method: `sinon.spy(obj, 'methodName')`


#### Example

```jsx
// Create the spy
let callback    = () => console.log('I’m still logged!')
let callbackSpy = sinon.spy(callback)

// Invoke the unit being tested
DomHelper.show(node, callbackSpy)

// Ensure the spy was called as expected
callbackSpy.callCount.should.eql(1)
callbackSpy.lastCall.args.length.should.eql(0)

// Restore the spy back to normal
callbackSpy.restore()
```


<br />

###### [More about spies](http://sinonjs.org/releases/v2.1.0/spies/)



<br />

### Mocks

Use mocks if and only if you are asserting on how a dependency is being used (i.e., expectations).

Do NOT use mocks if [spies](#Spies) or [stubs](#Stubs) suffice.

Do NOT abuse mocks. Using mocks in any complex way usually indicates a problem with the underlying code architecture.

<br />

###### [More about mocks](http://sinonjs.org/releases/v2.1.0/mocks/)



<br />

### Fixture mocks

Dummy objects that have pre-determined properties and no-op methods that mimic the top-level API of a module.

A fixture mock can be used to:

1. Emulate an environment, like iOS
* Mimic a module that is only available in certain environments, like Cordova plugins

Fixture mocks are primarily used with [dependency injections](#Dependency injections)



<br />

### Dependency injections

Replace dependencies of a module with an alternate that can be manipulated to ease testing.

A dependency injection can be a dummy object or a stubbed copy of the dependency.

Dependency injections are useful in two scenarios:

1. When the unit being tested passes data to a dependency
* When the unit being tested requires certain conditions to be true (such as an in-app environment)


#### Example

##### Replacing a dependency with a stub

```jsx
// modal.jsx

let DomHelper = require('assets/js/helpers/Dom')
module.exports = {
  open(node) { DomHelper.show(node, () => console.log('done')) }
}
```

```jsx
// modal.spec.jsx

let DomHelper     = require('assets/js/helpers/Dom')
let ModalInjector = require('inject!./modal')

// Inject the DomHelper so we can inspect how it’s used
let Modal = ModalInjector({
  'assets/js/helpers/Dom' : DomHelper
})

// Create the stub
let showStub = sinon.stub(DomHelper, 'show')

// Invoke the unit being tested
Modal.show(node)

// Ensure the stub was called as expected
showStub.callCount.should.eql(1)
showStub.lastCall.args.length.should.eql(2)
showStub.lastCall.args[0].should.be.exactly(node)
showStub.lastCall.args[1].should.be.of.type('function')

// Restore the stub back to normal
showStub.restore()
```

<br />

##### Emulating an environment

```jsx
// fixture-mocks/globals/client/ios.jsx

module.exports = {
  APP : true,
  IOS : true,
}
```

```jsx
// module.jsx

let client = require('globals/client')

if (client.IOS) {
  // ...
}
```

```jsx
// module.spec.jsx

let clientIos      = require('fixture-mocks/globals/client/ios')
let moduleInjector = require('inject!./module')

// Inject the iOS client fixture mock to emulate the environment
let module = moduleInjector({
  'globals/client' : clientIos
})
```


<br />

###### [More about dependency injections](https://github.com/plasticine/inject-loader)



<br />

### Module wrappers

Quite often, there are scenarios where a Cordova plugin is exported to the global namespace. Not only does this clobber the global namespace, but it also makes it more difficult to test (since those globals are not available in a testing environment).

To get around this, globals can be “wrapped” into a module:

```jsx
// module.jsx before using the wrapped module

module.exports = {
  openCamera() {
    window.StatusBar.hide()
  }
}
```

```jsx
// assets/wrappers/status-bar.jsx (the wrapped module)
module.exports = window.StatusBar
```

```jsx
// module.jsx after using the wrapped module

let StatusBar = require('assets/wrappers/status-bar')
module.exports = {
  openCamera() {
    StatusBar.hide()
  }
}
```

```jsx
// module.spec.jsx

let StatusBar      = require('fixture-mocks/wrappers/status-bar')
let moduleInjector = require('inject!./module')

// Now the status bar can be emulated by injecting the fixture mock
let module = moduleInjector({
  'assets/wrappers/status-bar' : StatusBar
})
```




<br />

---

<br />

## Libraries

1. [Mocha](https://mochajs.org/): the test suite
* [Karma](http://karma-runner.github.io/): the test runner
* [Sinon](http://sinonjs.org/): the spying library
* [Should.js](http://shouldjs.github.io/): the assertion library
