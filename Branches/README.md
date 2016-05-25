# Branches

We follow a variation of the traditional Git Flow branching model.

Type | Purpose | Pull ~> Push | Naming Convention
:----|:--------|:-------------|:-----------------
`master` | Latest stable code in production |  | `master`
`develop` | Latest stable code in development | `master` & release | `develop`
Release | Snapshot of `develop` to be used for a release | `develop` ~> `master` | `release/RELEASE_NAME`<br />Eg. `release/v3.3.0`
Feature | Congolomeration of a set of related subfeatures and bugfixes to be released together | `develop` ~> `develop` | `feature/FEATURE_NAME`<br />Eg. `feature/custom-workout`
Subfeature | Part of a feature | feature ~> feature | `feature/FEATURE_NAME.FEATURE_NAME`<br />Eg. `feature/custom-workout.search-filters`
Hotfix | Fix for a bug existing in production | `master` ~> `master` | `hotfix/HOTFIX_NAME`<br />Eg. `hotfix/workout-saves-endlessly`
Bugfix | Fix for a bug existing in `develop` | `develop` ~> `develop` | `bugfix/BUGFIX_NAME`<br />Eg. `bugfix/search-following-users`
Release Bugfix | Fix for a bug in a release *before* the release is published | release ~> release | `release/RELEASE_NAME.bugfix.BUGFIX_NAME`<br />Eg. `release/v3.3.0.bugfix.workout-saving`
Feature Bugfix | Fix for a bug introduced in a feature | feature ~> feature | `feature/FEATURE_NAME.bugfix.BUGFIX_NAME`<br />Eg. `feature/custom-workout.bugfix.workout-saving`

<br />
### Branching structure
This is an example branching structure. It shows which branches should be merged in to which and also which branches should be used as a base branch in your [Pull Request](/Pull Requests/README.md).

Example:
* Feature name      = _Workout_
* Subfeature name 1 = _Preview_
* Subfeature name 2 = _Builder_
* Subfeature name 3 = _Share_
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
- Each `◆` (diamond) repesents a merge. Either from the subfeature branch to the feature branch or from the feature branch to `develop`.

You must open a PR on your subfeature branch (eg. `feature/workout.preview`) against the feature branch (eg. `feature/workout`). After the [Code Review](../Code Review/README.md), the subfeature branch will be merged in to the feature branch and eventually the feature back in to `develop`.

<br />
### Pulling code from an upstream branch
**You must NEVER (EVER-EVER) pull into a subfeature branch from anywhere except for it’s relevant feature branch.**

When other developers merge code into `develop` after you create your feature, you will need to update your feature branch with the new code.
<br />

For example, `develop` **must not** be pulled into `feature/workout.preview` or `feature/workout.builder` directly. You must first pull `develop` into `feature/workout`, and then pull `feature/workout` into `feature/workout.preview` and `feature/workout.builder`.
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
- Each `◆` (diamond) repesents a merge. Either from the subfeature branch to the feature branch or feature branch to `develop`.
- The `◦` (empty dot) represents the upstream branch pull trail
     - First `develop` is pulled in to `feature/workout` and then in to `feature/workout.preview` and `feature/workout.builder`

<br />
### Permissions

In order to merge code into a branch, *you must have permission*.
Unfortunately, GitHub doesn't have all permissions built-in, but we devise our own and shoot any who merge without permission with Nerf™ guns.

1. **Gatekeeper**
  * Permission to merge into mission-critical branches, including `master`, `develop`, `release`, and `hotfix`
* **Developer**
  * Permission to merge into all other branches, including feature and subfeature branches

**If you have to ask if you're a gatekeeper, you're not a gatekeeper.**
