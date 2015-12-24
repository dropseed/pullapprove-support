---
date: "2015-12-11T23:39:09-06:00"
title: "YAML configuration"
menu: "sidebar"

---

## YAML settings configuration
To enable, simply place a `.pullapprove.yml` file in the root of your repo.

#### Custom reviewer settings and groups

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

<br>

## YAML Options
Be sure to check the settings page of your repo in https://pullapprove.com, it will tell you if there is an error
in your .pullapprove.yml file.

<br>

##### **approve_by_comment**
Enable parsing of pull request comments on github.com to trigger approval status.

**Default**: `false` **Possible values**: `true`, `false`

---

##### **approve_regex**
Set a custom regular expression to use when parsing pull request comments for approval.

> Note: `approve_by_comment` must be enabled to use this.

**Default**: `'^Approved'` **Possible values**: any valid regex, in a *single-quoted* string

---

##### **reject_regex**
Set a custom regular expression to use when parsing pull request comments for rejection.

> Note: `approve_by_comment` must be enabled to use this.

**Default**: `'^Rejected'` **Possible values**: any valid regex, in a *single-quoted* string

---

##### **reviewers**
This is a dynamic field for defining who reviewers are. See examples below for usage.

<br>

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
