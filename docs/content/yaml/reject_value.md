---
date: 2016-2-27T20:19:46-06:00
default_value: "0"
menu: yaml_settings
possible_values:
    - "any integer <= 0 (ex. -1)"
title: reject_value
---

Set a custom value for what a rejection is worth. Essentially allows rejections to cancel out approvals -- if set to -1, then every rejection would require 1 additional approval. If set to -2, then 1 rejection would require 2 more approvals.

#### Examples
Rejections cancel out approvals 1-for-1
```yaml
reject_value: -1
```

A single rejection rejects the PR (use any value > the number of reviewers you have)
```yaml
reject_value: -99
reviewers:
    required: 2
    members:
        - userone
        - usertwo
        - userthree
        - userfour
```
