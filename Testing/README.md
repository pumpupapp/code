# Legend

* [JavaScript Frontend](JavaScript Frontend.md)


## Questions


* What do and don't you test for?
  * Prioritizing
  * Private functions
* When do you test?
  * Before pushing? Merging? Releasing?
* How important is coverage vs depth?
* What is better: unit testing or integration testing?
* How do you test external dependencies?
  * Global dependencies
  * External APIs



## Types

### Unit Testing

* Testing a unit of code
  * Functions
  * Objects
  * Arrays
  * Modules
  * ...
* Minimalistic
* Covers all cases within the scope of the unit
  * Edge cases
  * Error handling
  * Not external code
* Examples:
  * Validators
  * Parsers
  * Checkers
* Advantages:
  * Exposes unexpected behaviour in the problem space
  * Easy to write, understand and maintain
* Disadvantages:
  * Tedious
  * Doesn't cover consumption of unit



### Integration Testing

* End-to-end testing
* Examples:
  * App UX flow
  * API request or collection of requests
* Advantanges:
  * Covers flow of units
  * Covers more of the codebase with less code
* Disadvantages:
  * Difficult to maintain because flows change
  * Scope is ambiguous



### Performance Testing

* Ensures code runs fast enough to meet a benchmark
* Fails when test takes longer than threshold to finish
* Examples:
  * API endpoint response time
  * Load testing
* Advantages:
  * Enforces speed
  * Exposes bottlenecks
* Disadvantages:
  * Difficult to simulate real environment
  * Time consuming to run
  * Difficult to maintain



## Unit Testing

Unit tests should be written before the unit is implemented. We use [TDD](https://en.wikipedia.org/wiki/Test-driven_development).

1. Create the unit skeleton
  * Define the function
  * Example: `function myFunctionToTest() {}`
* Define each pending test case
  * Determine expected inputs and outputs
* Commit and open a [PR](../Pull Requests/README.md)
  * Example: `:white_check_mark: [myModule] Define test cases for #myFunctionToTest`
* Implement each test case
  * Ensure they all fail
* Commit and open a **WIP** [PR](../Pull Requests/README.md)
  * Example: `:white_check_mark: [myModule] Implement test cases for #myFunctionToTest`
* Implement the unit
  * Ensure all tests pass
* Commit and open a [PR](../Pull Requests/README.md) to your **WIP**
  * Example: `:star: [myModule] Implement #myFunctionToTest`



### Defining

When defining test cases, one must look at every possible avenue that the code can take. These are called **boundaries**, and every function has _at least one_.

**Example:**

```jsx
function f(x) {

  if (x > 0) {
    return 1
  }

  if (x < 0) {
    return -1
  }

  return 0

}
```

In the above snippet, one would create 3 test cases:
```jsx
it('returns 1 when x > 0')


it('returns -1 when x < 0')


it('returns 0 when x is not < 0 or > 0')
```

In each of these test cases, it is important to test the **bounding value**.
```jsx
it('returns 1 when x > 0', () ={
  f(1).should.eql(1)
})


it('returns -1 when x < 0', () ={
  f(-1).should.eql(-1)
})


it('returns 0 when x is not < 0 or > 0', () ={
  f(0).should.eql(0)
})
```

It is not mandatory to test intermediate values, but it is encouraged.
```jsx
it('returns 1 when x > 0', () ={
  f(1).should.eql(1)
  f(10).should.eql(1)
  f(100000).should.eql(1)
  f(Infinity).should.eql(1)
})


it('returns -1 when x < 0', () ={
  f(-1).should.eql(-1)
  f(-10).should.eql(-1)
  f(-100000).should.eql(-1)
  f(-Infinity).should.eql(-1)
})


it('returns 0 when x is not < 0 or > 0', () ={
  f(0).should.eql(0)
  f(null).should.eql(0)
  f(false).should.eql(0)
  f(NaN).should.eql(0)
})
```

It is best to derive the test cases from the expected results _before_ implenting the unit.



### Structure

Every test case should follow this general structure.
NOTE: Each of these comments should be customized for every test case implementation.

```jsx
// Set up (optional)

// Run the unit

// Assert the output

// Clean up (optional)
```



### Adequacy

An easy way to see if your tests are adequate is to use a code coverage tool. If the unit you tested is not fully covered, more tests are required.

Otherwise, it is up to your [Code Review](../Code Reviews/README.md) to determine if your tests are adequate.



## Integration Testing

TODO


## Integration Testing

TODO