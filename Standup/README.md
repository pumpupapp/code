# Standup

## Description

A **Standup** is a summary of what you did the previous work day and what you will do during the current work day.


## Benefits

* Optimize communication of your daily plan
  * Coworkers can chime in if they think your standup requires changes
* Set goals for yourself every day
* Track your work progress
  * Use for summarizing your week in [Sprint Plans](../Sprint Plan/README.md)



## Requirements

* Must be posted every work day
* Must be posted in **#dev_standups**
* Must be posted within 1 hour of starting work on your computer
  * Failure to do so will result in an automatic fail



## Format

* **Yesterday <#>P|F**
  * Describe what you did the previous day
    * Clear and concise, yet thorough
  * Mark the day as **P**ass or **F**ail
    * Every time you accomplish all your goals from the day before, you earn a **P**
    * **P**s are compounded until you cash them in:
      * **20P = 1 Karma Star**
    * Once you hit 20P, they are automatically cashed in
    * When you don’t accomplish all your goals from the day before, you receive an **F**
      * This resets your **P** to 0
  * Example 1:
    * **Yesterday 6P**
      * Implemented and tested `Workout.completedCount` + private posts in following feed
  * Example 2:
    * **Yesterday F**
      * Failed to implement `Workout.completedCount`
* **Today**
  * Set your goals for the day
    * Maximum of 3 bullets
    * Don’t overestimate
  * Don't be afraid to make some optional
    * Eg. *Optional:* Finish parsing the push payload
  * Example:
    * **Today**
      * Finish writing Standup process
      * *Optional:* Push the new Standup process
* **Interesting** *(optional)*
  * Something interesting that you came across recently
  * Example:
    * **Interesting**
      * Yesterday I saw 2 hobos making out


Failure to post a standup may result in a gentle Nerf™ gun shot from a nearby developer. **Please avoid eye and genital contact.**
