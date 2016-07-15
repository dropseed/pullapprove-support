---
date: 2016-06-16T20:19:35-06:00
default_value: ""
menu: yaml_settings
possible_values: ""
title: signed_off_by
pro: yes
---

Require that all commits in the PR are signed-off-by their **git author** (i.e. commit message contains `Signed-off-by: Dave Gaeddert <dave.gaeddert@pullapprove.com>`, with an email address that matches the author).

Typically used to help manage compliance with http://developercertificate.org/.

> Note: This currently only checks the latest [250 commits on a PR](https://developer.github.com/v3/pulls/#list-commits-on-a-pull-request), if you have PR's larger than that, please let us know.

```yaml
signed_off_by:
    required: true
```
