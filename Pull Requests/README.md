# Pull Requests (PR)

A PR is a request to merge one branch into another.

It must contain:

* **Subject:** Summary of proposed changes
* **Comment:** Details of proposed changes
* **Assignee:** Person to perform a Code Review


#### When to PR

A PR **must** be opened when merging the following types of branches:

* feature branch ~> project branch
* project branch ~> `develop` **ONLY WHEN YOU HAVE COMPLETED INTERNAL QA**
* project bugfix branch ~> project
* release bugfix branch ~> release
* hotfix branch ~> `master`


#### When **not** to PR

A PR **must not** be opened when merging the following types of branches:

* `master` ~> `develop`
* release branch ~> `master`


## Rebase

When pulling changes from one stream to another (eg. `develop` ~> `master`), there are two ways to do so: a regular merge or a “rebase” merge.

Typically, you should always do a rebase merge.

The only exceptions are:

* project branch ~> `develop`
* release branch ~> `master`


## Culture

After opening a PR, it is customary to gently shoot the assigned *Reviewer* with a Nerf™ gun. **Please avoid eye and genital contact.**
