# Pull Requests (PR)

A PR is a request to merge one branch into another.

It must contain:

* **Subject:** Summary of proposed changes
* **Comment:** Details of proposed changes
* **Assignee:** Person to perform a [Code Review](Code Review)



## Checklist

To show that you respect your code reviewer's time, it's important that you make this process as quick and painless as possible for them. Before opening a PR, make sure you have done **all** of the following:

- [x] Re-read all of your changes and make sure everything is perfect
  - [x] Style
  - [x] Architecture
  - [x] Easy to read
- [x] Test your changes and make sure they work and don't introduce bugs
- [x] Ensure your code coverage has increased, and that any files you touched do not introduce missed lines
- [x] Run tests locally so that they don't fail when you make the PR




## DO open a PR

A PR **must** be opened when merging the following types of branches:

* feature branch ~> project branch
* project branch ~> `develop` **ONLY WHEN YOU HAVE COMPLETED INTERNAL QA**
* project bugfix branch ~> project
* release bugfix branch ~> release
* hotfix branch ~> `master`


## DO NOT open a PR

A PR **must not** be opened when merging the following types of branches:

* `master` ~> `develop`
* release branch ~> `master`


## Rebase

When pulling changes from one stream to another (eg. `develop` ~> `master`), there are two ways to do so: a regular merge or a “rebase” merge.

Typically, you should always do a rebase merge.

The only exceptions are:

* project branch ~> `develop`
* release branch ~> `master`
