# Branches

We follow a variation of the traditional Git Flow branching model.

Type | Purpose | Pull ~> Push | Naming pattern | Example
:----|:--------|:-------------|:---------------|:-------
Master | Latest stable code in production |  | `master`
Develop | Latest stable code in development | `master` & Release branch | `develop`
Release | Snapshot of `develop` | `develop` ~> `master` | `release/RELEASE_NAME` | `release/v3.3.0`
Project | Receives pull requests from feature & bugfix branches | `develop` ~> `develop` | `feature/PROJECT_NAME` | `feature/custom-workout`
Feature | Implements new feature | Project branch ~> Project branch | `feature/PROJECT_NAME.FEATURE_NAME` | `feature/custom-workout.search-filters`
Feature bug | Fixes a bug in a feature | Project branch ~> Project branch | `feature/PROJECT_NAME.bugfix.BUGFIX_NAME` | `feature/custom-workout.bugfix.workout-saving`
Release bug | Fixes a bug in a release | Release branch ~> Release branch | `release/RELEASE_NAME.bugfix.BUGFIX_NAME` | `release/v3.3.0.bugfix.workout-saving`
Hotfix | Fixes a bug in production | `master` ~> `master` | `hotfix/HOTFIX_NAME` | `hotfix/workout-saves-endlessly`