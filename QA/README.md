# QA


## Overview

The goal with QA is to ensure that every app update contains no regressions and all new functionality works.





## Process

### Mobile

1. Update the app version to `[VERSION]-[PROJECT_NAME].[BUILD_NUMBER]`, eg.
    ```
    yarn bump -- -v 5.3.0-payment-settings.0
    ```

1. Update the QA checklist in Trello
   1. Open the Trello `App Support` board
   1. Find `[QA] Testing Process` under the `Testing` list
   1. Add/change/remove all necessary checklists/checklist items
      * Suffix your changed items with the final version in brackets (eg. `(5.3.0)`)

1. Create a list in Trello with the format `[VERSION] Bugs`
   * This is where any bugs in the build will be posted

1. Build on iOS & Android
   * Follow instructions in `mobile/README.md` under `Build a packaged app in release mode`

1. Upload to exported archive to the Slack #testing channel
   * Use the name with the name equal to the QA app version

1. Monitor the `[VERSION] Bugs` list in Trello and fix any that come up

1. Ensure the app is fixed and fully tested
   * All checklist items are completed by testers

1. Merge your project and/or release the version
