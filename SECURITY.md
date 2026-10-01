# Security policy

## Reporting a vulnerability

Please do not open a public issue for a suspected vulnerability. Use the repository's private
GitHub vulnerability-reporting flow, or contact the support team through
[obsibrain.com](https://www.obsibrain.com) if private reporting is unavailable.

Include the affected version, impact, reproduction steps, and any suggested mitigation. Do not
include real license credentials, email addresses, or private vault content. Allow time for a fix
and coordinated disclosure before publishing details.

Only the latest published version is supported with security fixes.

## V1 importer boundary

The desktop migration wizard treats every external v1 vault as untrusted input. It resolves source
and target roots before analysis, rejects overlapping roots, blocks traversal and destination
collisions, and does not traverse symbolic links or junctions. It fingerprints source files before
planning and rechecks them before each target operation.

The importer never loads source plugins or evaluates source scripts. It recognizes a small static
allowlist of legacy blocks and preserves unknown executable content unchanged. Analysis writes
nothing. Import creates files sequentially through Obsidian vault APIs and never overwrites or
renames conflicting target content. Migration sends no data over the network.

## Obsibrain AI (Alpha) boundary

The optional Obsibrain AI (Alpha) desktop panel runs Pi CLI in RPC mode. Pi has no built-in sandbox, so Obsibrain starts
it with a strict tool boundary. The process disables discovered extensions, skills, prompts, themes,
context files, project trust, and every built-in tool.

Obsibrain embeds one trusted Pi extension in `main.js`. It writes that extension to a private
temporary directory before startup and removes the directory on shutdown. The extension exposes one
tool named `exec_command`.

`exec_command` accepts only allowlisted Obsidian CLI read and navigation commands. Every command is
pinned to the current vault. The extension blocks non-Obsidian programs, writes, vault overrides,
absolute paths, traversal, hidden paths including `.obsidian`, administrative commands, permanent
deletion, excessive output, and long-running commands. Report any bypass as a security issue.
