# Naming Things

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

...

- prefix
- postfix
- namespace


<br />

## Conventions in naming functions

...always prefix with a verb... these are some well-defined examples:


Prefix    | Action    | Parameters | Returns value  | Example   | Alternate prefixes
:---------|:----------|:-----------|:---------------|:----------|:---------------------
`create`  | creates something new | yes | yes | `let myCar = createCar('Tesla Model S')`
`build`   | builds something new on the instance of an object | optional | | `myCar.buildMotor()` | `setup`
`get`     | gets something | | yes | `user.getFullName()`
`set`     | sets a child property | yes | | `user.setFollowerCount(10)` | `increment`, `decrement`
`update`  | updates a parent | optional | | `user.updateProfilePhoto()` | `refresh`
`save`    | persists something to the DB
`convert` | changes something from one state to another | optional | the changed thing | `myCar....()`
`is` | to be or not to be? | | | `has`, `will`, `did`, `can`, `should`




<br />

## Examples

...

bad names... good names...
