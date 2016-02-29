---
date: 2015-12-30T20:55:15-06:00
default_value: "default"
menu: yaml_settings
possible_values:
    - "ignored"
    - "required"
title: author_approval
pro: no
---

Whether or not approval is required by the author of the pull request.

### Usage
##### default
The author can approve their own pull requests. Their approval counts towards the `required` number.

##### ignored
The author can approve their own pull requests, but it does not count towards the number of approvals `required`. For example, if 3 reviewers must approve a PR then that means 3 reviewers *excluding the author*.

##### required
The author **must** approve the pull request. Useful if PRs are opened "early and often" to facilitate discussion, despite the work being finished.
