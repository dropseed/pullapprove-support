---
date: 2015-12-30T20:19:42-06:00
default_value: "'^Approved'"
menu: yaml_settings
possible_values:
    - "any valid regex, in a *single-quoted* string"
title: approve_regex
---

Set a custom regular expression to use when parsing pull request comments for approval.

> Note: `approve_by_comment` must be enabled to use this.
