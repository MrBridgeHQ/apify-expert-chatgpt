# Installation - Apify Expert skill (ChatGPT / Codex)

This is a **ChatGPT / Codex skill**: a knowledge hub for Apify platform facts. It has no runtime dependencies - no Python, no packages, no network calls. Installation is just placing the folder where Codex discovers skills.

## Prerequisites

- ChatGPT Codex (or a compatible agent that loads Codex-format skills) installed and working.
- A terminal with `unzip` (macOS, Linux) or PowerShell with `Expand-Archive` (Windows).

## Installation

### macOS / Linux

```bash
# 1. Create the Codex skills directory if it doesn't exist
mkdir -p ~/.codex/skills

# 2. Unzip the skill into that directory
unzip apify-expert.zip -d ~/.codex/skills/

# 3. Verify the structure
ls ~/.codex/skills/apify-expert/
# Expected: SKILL.md  README.md  INSTALL.md  agents/  references/
```

### Windows (PowerShell)

```powershell
# 1. Create the Codex skills directory if it doesn't exist
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.codex\skills"

# 2. Unzip the skill into that directory
Expand-Archive -Path .\apify-expert.zip -DestinationPath "$env:USERPROFILE\.codex\skills\"

# 3. Verify the structure
Get-ChildItem "$env:USERPROFILE\.codex\skills\apify-expert\"
# Expected: SKILL.md  README.md  INSTALL.md  agents  references
```

> If your Codex installation expects skills in a different location, place the `apify-expert/` folder wherever your agent discovers skills. The `SKILL.md` file must sit at the root of that folder.

## Verification

Open a Codex session and ask:

> "What skills do you have access to?"

You should see `apify-expert` in the list. If not, check that `SKILL.md` is at the path:

- macOS / Linux: `~/.codex/skills/apify-expert/SKILL.md`
- Windows: `%USERPROFILE%\.codex\skills\apify-expert\SKILL.md`

## First test

In any Codex session, ask a platform-fact question, for example:

> "On Apify, how is CPU allocated relative to an Actor's memory setting?"

The skill should activate and answer from `references/platform-overview.md` (4096 MB = 1 full vCPU core; memory must be a power of two). A follow-up like "did anything change recently with Apify datasets?" should route to `references/changelog-digest.md`.

## How it activates

Activation is driven by the `description` field in `SKILL.md`'s frontmatter and by the `agents/openai.yaml` interface descriptor (which sets `allow_implicit_invocation: true`). If implicit activation misses, force it: "Use the `apify-expert` skill to…".

## Updating the skill

To install a newer version, replace the directory:

```bash
# macOS / Linux
rm -rf ~/.codex/skills/apify-expert
unzip apify-expert.zip -d ~/.codex/skills/
```

If you have hand-edited the `references/*` files (for example, to extend the changelog digest), back them up before replacing - your edits will be overwritten.

## Keeping the changelog digest current

`references/changelog-digest.md` is maintained **by hand**; no automated updater ships with this skill. Periodically review <https://apify.com/change-log>, add new entries newest-first under the `INSERT-NEW-ENTRIES-BELOW` marker, and update the baseline `references/*` files when an entry changes a fact they state.

## Uninstalling

```bash
# macOS / Linux
rm -rf ~/.codex/skills/apify-expert

# Windows (PowerShell)
Remove-Item -Recurse -Force "$env:USERPROFILE\.codex\skills\apify-expert"
```

## Support

This skill is a personal toolkit. To extend it, edit the `references/*.md` files directly - they are the authoritative surface. Verify drift-prone figures (flagged *(verify)*) against <https://docs.apify.com> before treating them as hard limits.
