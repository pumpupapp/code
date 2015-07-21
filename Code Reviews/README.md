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

1. **Developer** assigns **Reviewer** to PR.
* *Optional:* **Developer** shoots **Reviewer** with a Nerf™ gun.
* **Reviewer** reviews every change, making any necessary comments along the way.
* **Reviewer** assigns **Developer** to PR.
* *Optional:* **Reviewer** shoots **Developer** with a Nerf™ gun.
* If there are any comments, **Developer** responds to each comment with either a follow-up comment or a code change. Once another review is ready, go back to (1).
* **Reviewer** may request a demo of the proposed changes. If any bugs are found, **Developer** must fix fix them and demo again.
* **Reviewer** merges the PR and deletes the branch.


## Reviewer Guide

The quality of a CR depends on the **Reviewer**. An ideal **Reviewer** pays close attention to the following:

* Style
  - Does is look and read beautifully?
* Functionality
  - Does it work?
* Logic
  - Is it understandable?
* Organization
  - Is it where it belongs?
* Performance
  - Is there a case where it can get slow?
* Errors
  - Is there a case where it can break?
* Tests
  - Has every case been covered?

Don't be afraid to get nit-picky!