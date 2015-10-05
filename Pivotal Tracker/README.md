# Pivotal Tracker

A development tracking tool.

The tracking tools provided are:

- Epics: A tracker for each project.
- Stories: A tracker for issues to tackle in a project.
- Tasks: A tracker for tasks to accomplish to finish a story.


## Epics

An epic contains all stories that relate to a specific project.

#### Guidelines

* Be as specific as possible
  * Eg. If you found a bug with creating a workout, use the **custom workouts** epic instead of the **mobile** epic
* If there is no relevant epic or you are unsure, use the **support** epic
* Add multiple epics, if possible
  * Eg. The following can be tagged with **mobile** and **custom workouts**:

    > Others' workout titles are editable when you click them from the feed



<br />
## Stories

A story contains information of a particular feature, chore, bug, or release. It is usually provided with a description, requester, assignee, labels, etc.


#### Types

##### Feature

Any new or improved functionality.

How to estimate points? 1 point = 2 hours (round up)

Lifecycle:

1. Unstarted: Not yet started. If not assigned, take it, otherwise ask to take it
* Started: WIP
* Finished: Committed and pushed
* Delivered: Merged
* Accepted/Rejected: Demoed


##### Chore

Any task that does not add any new functionality or fix any existing functionality. An example is clean up, or work not related to code.


##### Bug

A report of broken functionality.

Write steps on how to reproduce in the description and, if helpful, attach screenshots.

(See [Feature](#Feature))


##### Release

A Project Release: a release tied to project epics that go into an App Release. Eg: Android Camera v1

An App Release: a version release that contains multiple Project Releases. Eg: 3.3



<br />
#### Title

* Starts with context in square brackets
* Descriptive
* Concise

##### Examples

> [Start Workout] Video doesn't autoplay after finishing first warmup exercise without audio

> [Find Friends] [Subscription] Remove find friends and subscription from app



#### Owners

People assigned to work on a story.



#### Description

Specific details of the story.



<br />
#### Labels

Quick tags to allow categorization and searching of stories.

* *Epic
* OS eg. **ios**
* Device eg. **iphone 6+**
* **regression** if it's something that used to work
* **cannot reproduce** if it's something that seems to have been fixed
* **sev-high** if it's something that is critical
* **sev-med** if it's something that isn't critical but is important
* **sev-low** if it's something that isn't important
* Version or date the build was taken from (eventually commit hash)

*Required



<br />
#### Tasks

A breakdown of a story into smaller actionable tasks that will collectively complete the story. Once all tasks are complete, the story should be marked as **Finished**.
