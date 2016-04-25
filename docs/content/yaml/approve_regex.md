---
date: 2015-12-30T20:19:42-06:00
default_value: "'^Approved'"
menu: yaml_settings
possible_values:
    - "any valid regex, in a *single-quoted* string"
title: approve_regex
pro: no
---

Set a custom regular expression to use when parsing pull request comments for approval.

Due to recent changes by GitHub, we now *automatically* check for the Unicode equivalents of emojis. For example, if you use `:\+1:` in your regex, we'll also check for `\U0001f44d`. **You do not have to add Unicode to your regular expressions.** An added bonus here is that alternative aliases will also be detected automatically, again if you use `:\+1:`, we'll also match if a team member uses `:thumbsup:`!

> Notes:
>
>    - `approve_by_comment` must be enabled to use this.
>    - We recommend starting with `^`, to only match strings at the beginning of a line. In our experience this makes approval more intentional, and also avoids issues with comments via email where previous content may be embedded in a blockquote (`>`) that could otherwise trigger mistaken approval.

#### Examples
Multiple triggers
```yaml
approve_regex: '^(Approved|:shipit:|:\+1:)'
```
