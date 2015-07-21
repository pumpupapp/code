# Code Reviews (CR)

> *Goes up to girl*
>
> Hey! I have a request: can you pull my branch?

A CR is a review of the proposed changes in a PR.

## Rules

1. A CR **must** be done before a PR can be merged.
* A CR **must not** be done by any authors of the PR.
* A PR **must not** be merged until all CI builds pass.


## Steps

1. *Developer* assigns *Reviewer* to PR.
* *Reviewer* goes through every change, making any necessary comments.
* *Reviewer* assigns *Developer* to PR.
* If there are any comments, *Developer* responds to each comment with either a follow-up comment or a code change. Once another review is ready, go back to (1).
* *Reviewer* may request a demo of the proposed changes. If any bugs are found, *Developer* must fix fix them and demo again.
* *Reviewer* merges the PR and deletes the branch.


## Reviewer Guide

The quality of a CR depends on the *Reviewer*. An ideal *Reviewer* pays close attention to the following:

* Style
  - Adherence to style guide
  - Typos
* Functionality
  - Works as proposed
* Logic
* Performance
* Errors
* Tests

Don't be afraid to get nit-picky!