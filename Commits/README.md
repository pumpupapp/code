# Commits

Commits **must** be:

* Modular
  * Easy to understand the changes made without having to jump between multiple commits.
  * Example: Renaming a function and renaming it everywhere that it is used should be a single commit.
  * Example: Two methods added to a module should be a single commit, but two unrelated methods are added to two separate modules should be two separate commits.
* Ordered
  * Independent of future commits.
  * Example: If Commit A introduces new functionality, and Commit B consumes the new functionality, then Commit A should be committed before Commit B.


<br />
## Messages


### Purpose
* Speed up the code review process
* Aid future maintainers
* Summarize changes over a release

### Structure

*Rule of thumb:* Commit message should answer the question: "What will this commit do?"

#### Subject

* Max 85 characters total (ie. -35 in Tower’s character count)

##### Order

1. Emoji(s)
  * Separate multiple with space
  * Use all that apply
    * :memo: writing docs
    * :bug: fixing a bug
    * :star: adding a feature
    * :art: tweaking the design
    * :sparkles: cleaning up
    * :white_check_mark: adding tests
    * :racehorse: improving perf
    * Use [others](http://www.emoji-cheat-sheet.com) sparingly
  * Eg. `:bug: :sparkles:`
* Context
  * Use familiar module title
  * Capitalized
  * Separate multiple with space
  * Eg. `[Edit Profile]`
* Text
  * Capitalized
  * Start with a verb
  * Present tense
  * Eg. `Fix unsaved changes popup when no unsaved changes`



#### Description *(optional)*

* Pivotal references (eg. `[Finishes #12345678]`)
* Extended description of commit
* Special cases:
  * `[ci skip]`
    * Prevents a CI build from being created
    * Useful for any changes that do not require a CI build
      * Eg. a documentation change


**Note: Every significant change should reference at least one Pivotal story.**


<br />
## Examples

```
// Subject
:bug: :white_check_mark: [/upload/workout] Fix workout photo upload for large photo + test

// Description
[Finishes #97240658]
````

```
// Subject
[ci skip] :memo: [Feed] Add documentation for feed view

// Description
[#12345678 #12345679]
```

```
// Subject
:sparkles: [Notification]

// No description
```
