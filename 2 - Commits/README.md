# Commits

Commits **must** be:
 
* Modular
	* Easy to understand what changes were made in a commit without having to jump between multiple commits.
	* Example: renaming a function and renaming it everywhere that it is used should be one commit.
	* Example: two methods added to a module should be one commit, but two unrelated methods are added to two separate modules should be two separate commits.
* Ordered
	* Independent of future commits.
	* Example: part one of changes introduce new functionality, and part 2 consumes the new functionality, then the first part should be committed before the second part.


## Commit Messages

* Purpose:
	* Speed up the code review process.
	* Aid future maintainers.
	* Summarize changes over a release.

* Structure:
	* Subject 75 characters
		* Present tense
		* Start with a verb
		* Prefix with emoji(s)
			* :memo: writing docs
			* :bug: fixing a bug
			* :star: adding a feature
			* :sparkles: cleaning up
			* :white_check_mark: adding tests
			* :racehorse: improving perf
			* Use others sparingly: http://www.emoji-cheat-sheet.com
	* Description (optional) that includes at least one pivotal story reference.

* Special cases:
	* `[ci skip]`: any changes that do not require a CI build.
		Example: a documentation change.

```
// Subject:
:bug: :white_check_mark: fix workout photo upload for large photo + test

// Description:
[finishes #97240658]
````

```
// Subject:
:memo: add documentation [ci skip]

// Description:
[#12345678 #12345679]
```

```
// Subject:
:sparkles:
```
		
**Note: every significant change should reference at least one Pivotal story.**



# pr process
(merge (not rebase) with project branch)

# cr process

# pivotal story process