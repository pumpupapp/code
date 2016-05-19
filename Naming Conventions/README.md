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
`bind` | does something when another thing happens | `bindOnOpenKeyboard(this.onKeyboardOpen)` | `on`
`convert` | changes something from one state to another | `convertDaoToFrontendObject(dao)` | `compress`, `normalize`, `parse`
`create` | creates something new | `createFollow(data)`
`delete` | deletes something from existence | `deleteWorkout(workoutId)` | `destroy`
`get` | gets something from another thing | `getUserName()` | `find`, `filter`, `copy`, `validate`, `match`
`initialize` | sets something to be in an initial state | `initialize()`
`is` | checks if something is another thing | `isModel(model)` | `has`, `will`, `did`, `can`, `should`
`load` | loads something from one place into another | `loadUserCache()` | `read`
`remove` | removes something locally but keeps in existence remotely | `removeAttachment(attachmentType)`
`save` | persists something to another thing | `save(path)` | `send`, `cache`
`set` | sets a child property | `setSearchText(searchText)` | `increment`, `decrement`, `update`, `toggle`, `clear`, `reset`, `sanitize`, `merge`, `mark`, `hellban`, `consume`




## Suffixes

Function and variable suffixes are slightly more ambiguous, but in most cases are standardized.


Suffix    | Description | Example   | Replaced prefixes/suffixes
:---------|:------------|:----------|:---------------------------
Entity | Name of thing being described | `Date` (`startDate`), `User` (`currentUser`), `Button` (`onClickLeftHeaderButton`), `Container`, `Util`
Reserved | Predefined names | `CreatedAt` (`lastCreatedAt`), `Id` (`currentUserId`)
`Count` | Number of instances of something | `unreadNotificationsCount` | `num`, `number`
`List` | Array | `followingList`