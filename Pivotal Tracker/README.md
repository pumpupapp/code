# Pivotal Tracker

A development tracking tool.

The tracking tools provided are:

- Epics: A tracker for each project.
- Stories: A tracker for issues to tackle in a project.
- Tasks: A tracker for tasks to accomplish to finish a story.


## Epics

An epic contains all stories that relate to a specific project.



## Stories

A story contains information of a particular feature, chore, bug, or release. It is usually provided with a description, requester, assignee, labels, etc.


### Types

#### Feature

Any new or improved functionality.

How to estimate points? 1 point = 2 hours (round up)

Lifecycle:

1. Unstarted: Not yet started. If not assigned, take it, otherwise ask to take it
* Started: WIP
* Finished: Committed and pushed
* Delivered: Merged
* Accepted/Rejected: Demoed


#### Chore

Any task that does not add any new functionality or fix any existing functionality. An example is clean up, or work not related to code.


#### Bug

A report of broken functionality.

Write steps on how to reproduce in the description and, if helpful, attach screenshots.

(See [Feature](#Feature))


#### Release

A Project Release: a release tied to project epics that go into an App Release. Eg: Android Camera v1

An App Release: a version release that contains multiple Project Releases. Eg: 3.3



### Title

* Starts with an action
* Concise



### Owners

People assigned to work on a story.



### Description

Specific details of the story.



### Labels

Quick tags to allow categorization and searching of stories.

* Epic: **this is required**
* OS
* Device
* Commit hash (if a bug) (TBD)




### Tasks

A breakdown of a story into smaller actionable tasks that will collectively complete the story.