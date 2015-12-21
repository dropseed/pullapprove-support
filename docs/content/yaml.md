---
date: "2015-12-11T23:39:09-06:00"
title: "YAML configuration"
menu: "sidebar"

---

## YAML settings configuration
To enable, simply place a `.pullapprove.yml` file in the root of your repo.

### Custom reviewer settings and groups

The biggest addition in this beta is the ability to define exactly who needs to review a PR.

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
reviewers:
    required: 1
    members:
        - a_user
        - anotheruser
```
