---
description: Take this project from "it works" to paying customers, step by step
argument-hint: "[step: offer | ship | pay | legal | ads | numbers]"
---

Use the `launch-playbook` skill.

1. Check the `shkor` MCP connection with `whoami`, as the skill describes.
2. Read `LAUNCH.md` at the repo root if it exists, and look at what's already in
   place (`product_list`, `git_repo_list`, whether the site opens). Work out which
   of the seven steps the project is on.
3. If the user named a step in `$ARGUMENTS`, go to it. Otherwise continue from
   the first unfinished step.
4. Do that one step to its "done when" condition, update `Status` in `LAUNCH.md`,
   and tell the user in two lines what's done and what's next.
