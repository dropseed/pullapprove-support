---
date: 2015-12-30T20:19:51-06:00
default_value: ""
menu: yaml_settings
possible_values: ""
title: reviewers
pro: no
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
        conditions:
            labels:
                - backend-review
            branches:
                - staging
    -
        name: designers
        required: 1
        members:
            - designerA
            - designerB
        conditions:
            files:
                - "*.png"
                - "*.jpg"

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

---

### Reviewer group settings

##### name
<div class="docs-yaml-values">Possible values: <span class="docs-yaml-value">any string</span></div>

A name to refer to this group of reviewers. Used in status messages. Optional if there is only one reviewer group.

---

##### required
<div class="docs-yaml-values">Possible values: <span class="docs-yaml-value">any integer >= -1</span></div>

The number of approvals required out of this group.

A value of `-1` means that approval is required from all members.

---

##### members
<div class="docs-yaml-values">Possible values: <span class="docs-yaml-value">array of username strings</span> <span class="docs-yaml-value">"all"</span></div>

The members of this reviewer group, by case-sensitive GitHub username.

A value of `all` means that all repo collaborators are reviewers in this group.

---

##### conditions

<div class="pro-required callout"><span class="fa fa-fw fa-level-up"></span> A <a href="https://pullapprove.com/pricing/">pro plan is required</a> to use conditions.</div>

- labels

    <div class="docs-yaml-values">Possible values: <span class="docs-yaml-value">array of label slugs</span></div>

    If any of these labels are present on the PR, this group must review the PR.

    ```yaml
    reviewers:
        -
            name: review-by-label
            required: 1
            members:
                - x
                - y
            conditions:
                labels:
                    - needs-review
    ```

- files

    <div class="docs-yaml-values">Possible values: <span class="docs-yaml-value">array of Unix shell-style strings</span></div>

    If any of these files were modified in the PR, this group must review the PR.

    File patterns written using Unix shell-style wildcards and matched using [Python's `fnmatch`](https://docs.python.org/2/library/fnmatch.html).

    ```yaml
    reviewers:
        -
            name: review-by-files
            required: 1
            members:
                - x
                - y
            conditions:
                files:
                    - "*.md"  # review if changed markdown files
                    - "docs/*"  # review if edited docs
    ```

- branches

    <div class="docs-yaml-values">Possible values: <span class="docs-yaml-value">array of branch names</span></div>
    If PR is merging into one of these branches, this group must review the PR.

    ```yaml
    reviewers:
        -
            name: review-by-branches
            required: 1
            members:
                - x
                - y
            conditions:
                branches:
                    - staging  # review if merging to staging
                    - deploy  # review if merging to deploy
    ```
