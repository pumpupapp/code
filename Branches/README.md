# Branches

We follow a variation of the traditional Git Flow branching model.

Type | Purpose | Pull ~> Push | Naming Convention
:----|:--------|:-------------|:-----------------
`master` | Latest stable code in production |  | `master`
`develop` | Latest stable code in development | `master` & Release branch | `develop`
Release | Snapshot of `develop` | `develop` ~> `master` | `release/RELEASE_NAME`<br />Eg. `release/v3.3.0`
Project | Receives pull requests from feature & bugfix branches | `develop` ~> `develop` | `feature/PROJECT_NAME`<br />Eg. `feature/custom-workout`
Feature | Implements new feature | Project branch ~> Project branch | `feature/PROJECT_NAME.FEATURE_NAME`<br />Eg. `feature/custom-workout.search-filters`
Feature bug | Fixes a bug in a feature | Project branch ~> Project branch | `feature/PROJECT_NAME.bugfix.BUGFIX_NAME`<br />Eg. `feature/custom-workout.bugfix.workout-saving`
Release bug | Fixes a bug in a release | Release branch ~> Release branch | `release/RELEASE_NAME.bugfix.BUGFIX_NAME`<br />Eg. `release/v3.3.0.bugfix.workout-saving`
Hotfix | Fixes a bug in production | `master` ~> `master` | `hotfix/HOTFIX_NAME`<br />Eg. `hotfix/workout-saves-endlessly`

NB: You must NEVER (EVER-EVER) pull from a grand-parent+ branch (e.g. Develop into feature/somefeature-someSubFeature. Always pull from the parent branch.

<br />
### Permissions

In order to merge code into a branch, you must have permission.
Unfortunately, GitHub doesn't have permissions built-in, but we devise our own and shoot any who merge without permission with Nerf™ guns.

1. **Gatekeeper**
  * Permission to merge into mission-critical branches, including `master`, `develop`, `release`, and `hotfix`
* **Developer**
  * Permission to merge into all other branches, including `project` and `feature`

**If you have to ask if you're a gatekeeper, you're not a gatekeeper.**
