Goal: Extract rules for our developer team based on our conversation.

Rules:
- List main rules to extract with the most value for the developer team.
- Use bullet points with short sentences.
- Output in expect format (replace `{placeholders}`)
- Be accurate and concise.

Expected format:
````mdc
---
file: {file-name-with.mdc}
description: {when to apply the rule}
globs: {which paths}
---

> {When }

## {Main rule}
- {rule 1}
- {rule 2}
- {rule 3}
...

## {Rule} : Example
```
...
```

````
