# energyquest — Beautiful Code Standard Audit

**Audit date:** 17 September 2026  
**Repository tier:** Active / normal game project  
**Standard:** The Beautiful Code Standard

## Overall finding

`energyquest` is a large Unity repository with a conventional Unity layout (`Assets`, `Packages`, `ProjectSettings`) but a messy repository boundary. It includes `UserSettings`, a Windows shortcut, a second `Energy Quest` directory and a roughly 98 MB `Racetrack.zip` in Git. Those artefacts make the repository heavier and less obvious than it needs to be.

The first Beautiful Code work here is repository hygiene and reproducibility, not metric optimisation.

## Findings

- **Obvious structure:** The core Unity structure is familiar, which is good.
- **Repository neatness:** `UserSettings`, a `.lnk` shortcut and a large ZIP are strong candidates for removal from source control unless there is a documented reason they are canonical project inputs.
- **One source of truth:** The coexistence of top-level Unity folders and a separate `Energy Quest` directory deserves review for duplicated project state or an obsolete copy.
- **Dependencies:** Unity package configuration should remain the dependency source of truth; avoid committing caches/build outputs.
- **Tests / CI:** No visible `.github` workflow or automated test evidence appeared in the audited tree. For an actively developed game, at least a project-open/build check is useful; gameplay smoke testing matters more than coverage percentages.
- **Large binary history:** The committed ZIP and numerous large media assets make ordinary Git history expensive. Genuine source assets belong in the repo, but exported archives/backups generally do not.

## Priorities

1. Decide which top-level Unity project is canonical and remove/archivalise duplicate project copies.
2. Remove generated/user-machine artefacts (`UserSettings`, shortcut files, exported ZIPs) unless there is a clear documented need.
3. Add/verify a Unity-aware `.gitignore` and use Git LFS for genuinely necessary large binary assets where appropriate.
4. Add a lightweight CI check that can open/compile/build the project or at minimum compile scripts, if the project is still active.
5. Add targeted Unity tests around real gameplay/system behaviour when bugs occur; do not chase generic coverage on asset-heavy game code.

## Bottom line

The code may be perfectly understandable inside Unity, but the repository currently carries too much non-source baggage. **Make the canonical project obvious and delete what Git does not need to remember.**
