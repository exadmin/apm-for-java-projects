---
description: Ensure IDE files are not tracked by git.
applyTo: ".idea/*.xml,.gitignore"
---

# IntelliJ IDEA project files
Before doing commit, push operations or after pull -  always check if ".idea/*.xml" files already tracked by git or not.
If tracked then ask user to drop git index for them by calling "git rm --cached -r .idea" and commiting changes.
Then add ".idea/" to ".gitignore" file.
