---
layout: page
---

To find images with multiple extensions - `jpg`, `jpeg` and `png` with the
format `*-{0-9}+.extension`.

```bash
find . -regextype sed -regex ".*/.*-[[:digit:]]\+.\(jpg\|png\|jpeg\)"
```
