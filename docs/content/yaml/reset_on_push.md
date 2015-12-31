---
date: 2015-12-30T20:55:54-06:00
default_value: "false"
menu: yaml_settings
possible_values:
    - "true"
    - "false"
title: reset_on_push
---

Whether or not approval statuses get reset to "pending" when new commits are pushed to a PR. If `false`, the PR effectively gets approved once. If `true`, any time new commits are pushed, those changes will need to be approved.
