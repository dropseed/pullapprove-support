---
date: 2016-05-35T20:19:35-06:00
default_value: ""
menu: yaml_settings
possible_values: ""
title: always_pending
pro: yes
---

A pull request matching any of these conditions will always have a "pending" status. Extremely useful for "work in progress" PR's.

PR's can be matched by either their title (with a regex) or labels. You can use the `explanation` field if you want to write your own status message.

```yaml
always_pending:
    title_regex: '(WIP|wip)'
    labels:
        - wip
    # custom message that will be used for the GitHub status
    explanation: 'This PR is a work in progress...'
```
