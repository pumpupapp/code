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

<br />
### Branching structure
This is an example feature branching structure. It shows which branches should be merged in to which and also which branches should be used as a base branch in your [Pull Request](/Pull Requests/README.md).

Example:
* Project name = _Workout_
* Feature name 1 = _Preview_
* Feature name 2 = _Builder_
* Feature name 3 = _Share_
```
 develop ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ◆ ~ ~ ...
                \                                                    |\
                 \                                                   | \
                  \                                                  |  \
                   \                                                 |   -- feature/...
   feature/workout  -- ~ ~ ~ ~ ~ ~ ~ ◆ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ◆ ~ ~ ~ ~ ◆
                      \              |\                    |\        |
                       \             | \                   | \       |
                        \            |  \                  |  \      |
                         \           |   \                 |   \     |
feature/workout.preview → • - - - - -•    \                |    \    |
                                           \               |     \   |
                  feature/workout.builder → • - - • - - - -•      \  |
                                                                   \ |
                                                                    \|
                                            feature/workout.share →  •
```
- Each `•` (bullet) represents a commit on the respective branch.
- Each `◆` (diamond) repesents a merge. Either from the feature branch to the project branch or project branch to develop.

You must open a PR on your feature branch (eg. `feature/workout.preview`) against the project branch (eg. `feature/workout`). After the Code Review, the feature branch will be merged in to the project branch and eventually the project branch back in to the develop branch.

<br />
### Pulling code from an upstream branch
**You must NEVER (EVER-EVER) pull into a feature branch from anywhere except for it’s relevant project branch.**

In the highly likely event that other developers merge code in to the `develop` branch after you create your project branch, you will need to update your project branch with the new code.
<br />

For example, `develop` **must not** be pulled into `feature/workout.preview` or `feature/workout.builder` directly. You must first pull `develop` into `feature/workout` and then pull `feature/workout` into `feature/workout.preview` or `feature/workout.builder`.
```
 develop ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ~ ◆ ~ ~ ~ ~ ~ ◆ ~ ~ ~ ~ ◆ ~ ~ ~ ~ ~  ◆ ~ ~ ...
                \               ◦                     ◦            |\
                 \               ◦                     ◦           | \
                  \               ◦                     ◦          |  \
                   \               ◦                     ◦         |   -- feature/...
  feature/workout  -- ~ ~ ~ ~ ~ ~ ~ ◆ ~ ~ ◆ ~ ~ ~ ~ ~ ~  ◆ ~ ~ ~ ~ ◆
                      \             ◦     |\             ◦         |
                       \            ◦     | \            ◦         |
                        \           ◦     |  \           ◦         |
                         \          ◦     |   \          ◦         |
feature/workout.preview → • - - - - ◆ - - •    \         ◦         |
                                                \        ◦         |
                       feature/workout.builder → • - • - ◆ - - - - •
```
- Each `•` (bullet) represents a commit on the respective branch.
- Each `◆` (diamond) repesents a merge. Either from the feature branch to the project branch or project branch to develop.
- The `◦` (empty dot) represents the upstream branch pull trail
     - First `develop` is pulled in to `feature/workout` and then in to `feature/workout.preview` and `feature/workout.builder`

<br />
### Permissions

In order to merge code into a branch, you must have permission.
Unfortunately, GitHub doesn't have permissions built-in, but we devise our own and shoot any who merge without permission with Nerf™ guns.

1. **Gatekeeper**
  * Permission to merge into mission-critical branches, including `master`, `develop`, `release`, and `hotfix`
* **Developer**
  * Permission to merge into all other branches, including `project` and `feature`

**If you have to ask if you're a gatekeeper, you're not a gatekeeper.**
