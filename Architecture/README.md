# Architecture

![](http://www.businessballs.com/images/treeswing/tree-swing-s-hogh.jpg)

What is architecture? How things work.

What is the goal of architecting *before* coding?
* 80:20
* Spend more time figuring out *how* your code will work
* Spend less time writing code

But really...
* Reduce time spent rewriting code
* Improve code quality and cohesion
* Future-proofing code



## Steps

1. What is the goal of the feature?
  * Example: GPS
    * Track and display all of the user's GPS motion activities automatically

* What are the sub-features of the feature?
  * What is necessary for the feature to operate
  * What other features need to work with this feature (now or in the future)
  * What existing functionality is there that can be reused for this feature
  * Example: GPS
    * Track an activity (in background)
    * Differentiate between activities
    * Store the activity data
    * Compress the data before storing it
    * Send the data to the server
    * Retrieve the data from the server
    * Display the activity data in <Widget>
    * Display the activity data in <Post>

* How will everything work together?
  * Research available technologies to implement every sub-feature and pick best option
  * Determine all functionality required by all sub-features
  * Example:
    * Display the activity data in <Widget>
      * Display the icon, calories, and time for every activity
    * Display the activity data in <Post>
      * Display the icon, calories, and time for a single activity

* Group common functionality
  * Example:
    * Both <Widget> and <Post> need to display the icon, calories, and time for an activity




## Process

1. Draft the architecture for the feature
  1. Create a new file, `architecture/FEATURE_NAME.md`
    * Example: `architecture/GPS.md`
  * Describe feature goal
  * List sub-features
  * Outline files
    * Function signatures
    * Data formats
    * Flow
  * Use PumpUp's MindManager template?
* Present the architecture to a qualified party
  1. Make a [Pull Request](/Pull Requests/README.md) from [feature branch to project branch](/Branches/README.md)
  * Assign a qualified party
* Implement the feature
