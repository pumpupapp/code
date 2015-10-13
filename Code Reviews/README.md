# Code Reviews (CR)

A CR is a review of the proposed changes in a [PR](/Pull Requests/README.md).

*It is the responsibility of the Code Reviewer to ensure that no bad code enters the codebase.*

## Rules

1. A CR must be **completed** before a PR can be merged.
* A CR cannot be performed by any **authors** of the PR.
* A PR cannot be merged until **all CI builds pass.**
* A CR must be performed by the Reviewer **within 24 hours** of assignment.


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
  - Does it read beautifully?
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
