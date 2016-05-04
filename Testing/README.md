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

### Unit testing

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



### Integration testing

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



### Performance/benchmark testing

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



## Steps to writing a unit test

* Following TDD (Test Driven Development), the tests should be written before the actual unit code is written

1. Create the unit skeleton
  * Example: Define the function
* Write out each pending test case
  * Determine expected inputs and outputs
* Implement each test case
  * Ensure they all fail
* Implement the unit
  * Ensure all tests pass



## Test case generation

NOTE: Each of these comments should be changed to reflect the test case implementation.

```jsx
// Set up

// Run the unit

// Assert the output

// Clean up
```



## Test adequacy



## Examples


