---
date: "2016-02-04T19:59:38-06:00"
title: "YAML templates"
menu: "sidebar"

---

## YAML templates

Templates are a great way to keep the key preferences for your organization in one location, and easily extend them on a per-repo basis.

Templates are created and managed on pullapprove.com. **You can find edit templates at pullapprove.com/YOUR_ORG** or by clicking your organization name when browsing repos on pullapprove.com.

An example template to contain some general rules for your organization.

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

Then for each repo, you simply create a .pullapprove.yml which `extends` one of your templates. Any settings in this file will then override the defaults provided by the template.

#### Repo .pullapprove.yml
```yaml
extends: client-projects
reset_on_push: false  # on this repo, we don't want to reset approvals on push
```
