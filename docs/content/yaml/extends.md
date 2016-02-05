---
date: 2016-02-04T20:19:35-06:00
default_value: ""
menu: yaml_settings
possible_values:
    - "any string matching a template name"
title: extends
---

Extend a [YAML template](/yaml-templates).

Any settings including in the same .pullapprove.yml will override the settings in the template (if they exist).

#### Repo .pullapprove.yml
```yaml
extends: client-projects
reset_on_push: false  # on this repo, we don't want to reset approvals on push
```

#### YAML template named "client-projects"
```yaml
approve_by_comment: true
approve_regex: '^(Approved|:\+1:)'
reset_on_push: true
reviewers:
    required: 1
    members:
        - davegaeddert
        - joelgaeddert
```
