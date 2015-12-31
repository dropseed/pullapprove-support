---
date: "2015-12-11T23:39:09-06:00"
title: "YAML overview"
menu: "sidebar"

---

## YAML settings configuration
To enable, simply place a `.pullapprove.yml` file in the root of your repo.

Be sure to check the settings page of your repo in https://pullapprove.com, it will tell you if there is an error in your .pullapprove.yml file.

Read details about each YAML setting on their respective pages, available in the menu on the left side of the page.

#### Example .pullapprove.yml
```yaml
approve_by_comment: true
approve_regex: '^:\+1:'
reject_regex: '^No'
reset_on_push: true
author_approval: ignored
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
