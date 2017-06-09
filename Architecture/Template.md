# [Feature Title]



## Description

This is the general "what?" of the feature. What is your feature? Why is it important? Keep it brief and to-the-point.

**Start Date               : DD/MM/YYYY**

**Expected Completion Date : DD/MM/YYYY**

**Actual Completion Date   : [TBD]**



## Post-Mortem

* Mistakes
  * This should be updated as you implement the feature
  * Add anything that you missed in your original architecture
* Challenges
  * This should be updated as you implement the feature
  * Add anything that was more challenging than expected, and may have contributed to misjudgement of time
* Metrics
  * List the metrics changes that arose after the feature was shipped
  * Don't forget to compare them with your expectations
* Learnings
  * Jot down what you learned in architecting and building this feature
  * How will you improve in future feature architectures and implementations?



## Goals

* The "why?" of this feature
* Point form
* High-level
* Not more than 5



## Metrics

* Actions
  * Added
    * Every new action name
    * Eg. `CONVERSATION_OPENED { isRead }`
  * Changed
    * How every changed action was modified
    * Eg. `SIGNUP` segmented by `{ type: 'email'|'facebook' }`
  * Removed
    * Every removed action name
    * Eg. `FACEBOOK_SIGNUP`
* Expectations
  * More
    * Actions you expect to see more of
  * Less
    * Actions you expect to see less of




## R&D

* Problem: Ask every question that you can think of regarding this feature and the challenges involved in implementing it
  * Describe results you obtained through research and development
    * What frameworks did you try? Why?
    * What information did you gather? StackOverflow answers, videos, GitHub comments, etc.
    * What assumptions did you make? How did they change? Why?
    * What had to be reverted? Why?
  * Solution: What was the final solution? Why did you pick it? List any sources.




## Flow

1. This is the "when?" and "where?" of this feature
* This happens first
* Then this
* And so forth




## Sub-Features

* [ ] This is the specific "how?" and "what?" of this feature
* [ ] Break it down
  * [ ] How will you achieve your goals?
* [ ] Be as specific as possible
  * [ ] Solve all problems before they occur and discover overlappings
* [ ] These checkboxes are then checked off as you implement the feature
  * [ ] The feature is complete once all checkboxes are checked, meaning *nothing* should be missing from this list
* [ ] Once your architecture is merged, these must be moved to stories in Pivotal Tracker
* [ ] Eg. `<ConversationsContainer>`: A container that will act as the root for the new `<Stack>`, left of `<NotificationsContainer>`




## Migration (optional)

* How will the current architecture be modified to migrate to this new architecture?
* What files will be removed?
* What functions will be deprecated?




## API


### [API Section 1 (Eg. Public, Private, Store)]

Provide the appropriate constants/variables/functions/etc. and their locations.
```js
// NOTE: Be sure to alphabetize your api sections.

/**
 * Fully document everything. This code is copy-pasteable for when
 * you begin the implementation phase.
 * @return {Boolean}
 */
function yoMama() {}
```


### [API Section 2]


Here is an example of a changed file:
```js
// ...

/**
 * This is a new function in an existing file. It is optionally wrapped in `// ...`.
 * @return {Any}
 */
function newFunction() {}

// ...

const EXISTING_CONSTANT = {

  // ...

  /**
   * This is a new property. Notice that it is surrounded by `// ...` to show
   * that it is modifying existing code.
   * @type {Object}
   */
  myNewProp: {},

  // ...

}
```
