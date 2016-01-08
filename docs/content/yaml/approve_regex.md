---
date: 2015-12-30T20:19:42-06:00
default_value: "'^Approved'"
menu: yaml_settings
possible_values:
    - "any valid regex, in a *single-quoted* string"
title: approve_regex
---

Set a custom regular expression to use when parsing pull request comments for approval.

> Notes:
>
>    - `approve_by_comment` must be enabled to use this.
>    - We recommend starting with `^`, to only match strings at the beginning of a line. In our experience this makes approval more intentional, and also avoids issues with comments via email where previous content may be embedded in a blockquote (`>`) that could otherwise trigger mistaken approval.

#### Examples
Multiple triggers
```yaml
approve_regex: '^(Approved|:shipit:)'
```
