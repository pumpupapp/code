# Pull Requests

A Pull Request is a request to merge one branch into another.

It must contain:

* Subject: Summary of proposed changes
* Comment: Details of proposed changes
* Assignee: Person to perform a Code Review


### When to create Pull Requests

A Pull Request **must** be opened when merging the following types of branches:

* feature branch ~> project branch
* project branch ~> `develop`
* project bugfix branch ~> project
* release bugfix branch ~> release
* hotfix branch ~> `master`


### When **not** to create Pull Requests

A Pull Request should **not** be opened when merging the following types of branches:

* `master` ~> `develop`
* release branch ~> `master`


## Pulling from one stream to another

When pulling changes from one stream to another, there are two ways to do so: a regular merge or a “rebase” merge.

Typically, you should always do a rebase merge.

The only exceptions are:

* project branch ~> `develop`
* release branch ~> `master`