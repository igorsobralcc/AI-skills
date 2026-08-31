Synchronize my personal Codex skills with:

[https://github.com/igorsobralcc/AI-skills.git](https://github.com/igorsobralcc/AI-skills.git)

Use the following rules:

1. The canonical local repository must be: $HOME.ai-skills

2. The personal Codex skills directory must be: $HOME.agents\skills

3. If $HOME.agents\skills does not exist, create it.

4. If $HOME.ai-skills does not exist, clone the repository there.

5. If the repository already exists:

   - fetch origin
   - compare the local main branch with origin/main
   - if there are no changes, do not modify anything
   - if origin/main contains new commits, fast-forward the local main branch
   - never force reset, discard local modifications, or overwrite uncommitted changes
   - if local modifications exist, stop and report the conflict instead

6. Discover skills recursively by finding directories containing SKILL.md beneath: $HOME.ai-skills\skills

7. For every discovered skill, ensure a corresponding directory exists directly beneath: $HOME.agents\skills\<skill-name>

8. Prefer directory junctions on Windows pointing from: $HOME.agents\skills\<skill-name> to the actual skill directory inside $HOME.ai-skills.

9. Do not overwrite unrelated personal skills already present in $HOME.agents\skills.

10. If a name collision exists with a directory that is not managed by this repository, leave it unchanged and report it.

11. Remove stale junctions only when:

- they point inside $HOME.ai-skills, and
- the referenced skill no longer exists in the repository.

12. Validate after synchronization:

- every managed skill points to an existing directory
- every managed skill contains SKILL.md
- report how many skills are installed
- report the previous and current Git commit when an update occurred

13. If nothing changed, finish with a short "Skills already up to date" result.

Do not modify the AI-skills repository contents. Do not commit, push, create branches, or change the remote repository.

# Take these steps and create a daily scheduled job that runs at <insert-preferred-hour-here>