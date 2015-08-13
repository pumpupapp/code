# Commits

Commits **must** be:

* Modular
	* Easy to understand the changes made without having to jump between multiple commits.
	* Example: Renaming a function and renaming it everywhere that it is used should be a single commit.
	* Example: Two methods added to a module should be a single commit, but two unrelated methods are added to two separate modules should be two separate commits.
* Ordered
	* Independent of future commits.
	* Example: If Commit A introduces new functionality, and Commit B consumes the new functionality, then Commit A should be committed before Commit B.


## Messages


### Purpose
* Speed up the code review process
* Aid future maintainers
* Summarize changes over a release

### Structure

*Rule of thumb:* Commit message should answer the question: "What will this commit do?"

#### Subject

* Max 75 characters
* Lowercase
* Present tense (eg. `fix` instead of `fixed`)
* Start with a verb
  * Eg. `add function to get workout name` instead of `workout name function`
* Prefix with emoji(s)
	* :memo: writing docs
	* :bug: fixing a bug
	* :star: adding a feature
	* :art: tweaking the design
	* :sparkles: cleaning up
	* :white_check_mark: adding tests
	* :racehorse: improving perf
	* Use [others](http://www.emoji-cheat-sheet.com) sparingly

#### Description *(optional)*

* Pivotal references (eg. `[finishes #12345678]`)
* Extended description of commit
* Special cases:
	* `[ci skip]`
	  * Prevents a CI build from being created
	  * Useful for any changes that do not require a CI build
	  	* Eg. a documentation change


**Note: Every significant change should reference at least one Pivotal story.**


## Examples

```
// Subject
:bug: :white_check_mark: fix workout photo upload for large photo + test

// Description
[finishes #97240658]
````

```
// Subject
[ci skip] :memo: add documentation for feed view

// Description
[#12345678 #12345679]
```

```
// Subject
:sparkles:

// No description
```
