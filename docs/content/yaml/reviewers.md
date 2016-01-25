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

### Reviewer group settings

##### name
<div class="docs-yaml-values">Possible values: <span class="docs-yaml-value">any string</span></div>

A name to refer to this group of reviewers. Used in status messages. Optional if there is only one reviewer group.

---

##### required
<div class="docs-yaml-values">Possible values: <span class="docs-yaml-value">any integer > -1</span></div>

The number of approvals required out of this group.

A value of `-1` means that approval is required from all members.

---

##### members
<div class="docs-yaml-values">Possible values: <span class="docs-yaml-value">array of username strings</span> <span class="docs-yaml-value">"all"</span></div>

The members of this reviewer group, by GitHub username.

A value of `all` means that all repo collaborators are reviewers in this group.

---

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
