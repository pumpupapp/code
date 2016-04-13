# Naming Conventions

As trivial as it may sound, naming things appropriately is one of the most difficult and important parts of writing good code.

> There are only two hard things in Computer Science: cache invalidation and naming things.
>
> \-- Phil Karlton


<br />

## Why is it so important?

A name of a thing tells you it’s purpose. If you misname it or name it something vague, it’s purpose becomes vague and more difficult to comprehend. This is very often the root cause of a lot of obscure bugs.

To aid with this, we follow a bunch of naming conventions.

These conventions force you to critically think about the purpose of something before you begin writing it. As a result, you’ll find yourself being much more explicit with how you use it — which leads to code that is modular and easy to read and debug.


<br />

## Conventions in naming

* Follow conventions
  * Pretty please
* Use existing prefixes/postfixes
* Name everything relative to the current context
  * For example, in `users.jsx`, the function `loadBatch` loads a batch of users


<br />

## Prefixes

Functions should always be prefixed with a *verb*. Before using a new verb, ensure it doesn’t fall under any of the ones below.


Prefix    | Action    | Example   | Alternate prefixes
:---------|:----------|:----------|:---------------------
`convert` | changes something from one state to another | `convertDaoToFrontendObject(dao)`
`create` | creates something new | `createFollow(data)`
`delete` | deletes something from existence | `deleteWorkout(workoutId)` | `destroy`
`get` | gets something | `getUserName()`
`initialize` | sets something to be in an initial state | `initialize()`
`is` | checks if something is another thing | `isModel(model)` | `has`, `will`, `did`, `can`, `should`
`load` | loads something from somewhere into another place | `loadUserCache()`
`remove` | removes something locally but keeps in existence remotely | `removeAttachment(attachmentType)`
`save` | persists something to the DB | `save(path)`
`set` | sets a child property | `setSearchText(searchText)` | `increment`, `decrement`, `update`, `toggle`, `clear`, `reset`

Honorable mentions (that can also be used):
* `bind`
* `copy`
* `filter`
* `find`
* `merge`
* `on`*
* `parse`
* `validate`
* Any special terminology, including (but not limited to) `compress`, `hellban`, `mark`, `match`, `normalize`, `read`, `send`, etc.


\* Used for event handlers
