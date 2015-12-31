---
date: 2015-12-30T20:19:51-06:00
default_value: ""
menu: yaml_settings
possible_values: ""
title: reviewers
---

This is a dynamic field for defining who reviewers are. See examples below for usage.

Overview:

- add as many "reviewer groups" as you like
- for each group:
    - give it a name
    - decide how many approvals are required
    - choose the members
- once approval has passed for all groups, the PR is approved

The structure is simple, yet powerful. Best explained by examples:

- require approval from 1 frontend dev, 1 backend dev, 1 admin
- require approval from 2 data scientists and 2 data engineers
- require approval from 2 developers, 1 consultant, 2 account managers
- require approval from...

#### Multiple reviewer groups example
```yaml
approve_by_comment: true
approve_regex: '^:\+1:'
reject_regex: '^No'
reviewers:
    -
        name: admins
        required: 2
        members:
            - a_user
            - anotheruser
    -
        name: backend_devs
        required: 1
        members:
            - backender_one
    -
        name: designers
        required: 1
        members:
            - designerA
            - designerB

```

#### Single reviewer group example
```yaml
approve_by_comment: false
approve_regex: 'LGTM'
reviewers:
    required: 1
    members:
        - a_user
        - anotheruser
```
