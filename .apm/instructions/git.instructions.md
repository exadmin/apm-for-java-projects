---
description: Git usage specific
applyTo: [".idea/*.xml", ".gitignore"]
---

# IntelliJ IDEA project files
Always add ".idea/" to ".gitignore" file.
If you see that ".idea/*.xml" files already tracked by git - advise user to drop git index for them by calling "git rm --cached -r .idea" and commiting changes.
