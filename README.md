# Obsibrain

Independent plugin for Obsidian, developed by Pierre Mouchan. Manage tasks, habits,
projects, goals, and periodic reviews with native dashboards and editable Markdown
templates. Obsibrain is not affiliated with or endorsed by Obsidian.

Full access requires a paid [Obsibrain](https://obsibrain.com) purchase and license
activation with your purchase email and license key. This plugin is proprietary
and closed source. Existing views remain readable without a valid license;
creation, mutations, AI, and the current built-in updater require a valid or
cached license. Initial activation requires internet access. Cached validation
permits up to 30 days of offline use.

## Features

- Native task tables with completion, editing, recurrence, and habit tracking.
- Projects with a Markdown outcome and completion derived from internal and linked tasks.
- Goals with explicit completion and separate task and project progress.
- Daily, weekly, monthly, quarterly, and yearly reviews.
- Editable templates under `templates/obsibrain`.
- A root dashboard and widget library for views inside Markdown notes.
- Typed notes for projects, goals, areas, resources, meetings, people, and general notes.
- Active-session reminders while Obsidian is open.
- Optional read-only vault chat through Pi on desktop.
- English, French, German, Spanish, Portuguese, Arabic, Japanese, Korean, and Chinese.

No mandatory community-plugin dependency is required.

## Requirements

- Obsidian 1.13.7 or newer.
- macOS, Windows, Linux, iOS, or Android.
- A paid Obsibrain license for full access.

AI and v1 import are desktop-only. AI also requires Obsidian CLI, Pi CLI 0.84.2
or newer, and authentication with a model provider through Pi. Provider accounts
and fees depend on your configuration.

## Installation

1. Open the vault where you want to use Obsibrain v2.
2. If Obsibrain v1 is enabled, disable it first.
3. Download `main.js`, `manifest.json`, and `styles.css` from a matching [v2 release](https://github.com/pierremouchan/obsibrain/releases).
4. Place all three files in `.obsidian/plugins/obsibrain` inside that vault.
5. Reload Obsidian and enable Obsibrain under **Settings → Community plugins**.
6. Enter your purchase email and license key in the activation dialog.
7. Reload Obsidian after activation to finish licensed startup and create any missing default templates.

## First use

Open the command palette and run **Obsibrain: Open Dashboard**.
Use **New Daily Planning**, **New Project**, or **Add Tasks and Habits** to start.
Use **Open Widget Library** to add a view to a note.

Edit templates under `templates/obsibrain` to change the content that creation
commands produce. Obsibrain creates missing defaults but never overwrites an
existing template. Note identity comes from frontmatter, so notes can live in
folders you choose.

For AI, run Pi and use `/login` before opening **Open Obsibrain AI (Alpha)**.
The panel asks for consent before its first message in a vault. AI reads vault
content through guarded Obsidian CLI commands and cannot edit notes. Source
links open the notes used in an answer.

## Upgrading from v1

V2 uses the ID `obsibrain`; v1 uses `obsibrain-plugin`. V2 stops before any vault
or settings write if v1 remains enabled in the same vault. Disable v1, then reload
Obsidian. Your license carries over on the same device.

On desktop, open **Settings → Obsibrain → Migration** to analyze an external v1
vault from versions `1.2.0` through `1.3.0`. Analysis writes nothing and requires
no license. Import requires a valid or cached license. It creates recognized
content in the current vault without changing the source or overwriting target
files. Review the preview and local report for unsupported workflows.

V1 releases remain in [obsibrain-plugin](https://github.com/pierremouchan/obsibrain-plugin).
That release channel receives no further updates.

## Network use and privacy

The plugin makes these requests when the related feature runs:

- License activation and validation send your purchase email and license key, or stored credential, to `https://www.obsibrain.com/api/validate-license` to verify access.
- Completion of onboarding sends your stored purchase email to `https://www.obsibrain.com/api/onboarding-finish`.
- The current built-in updater queries the GitHub API for `pierremouchan/obsibrain` and downloads release assets from GitHub. Automatic installation defaults on and has a settings toggle.
- Optional desktop AI uses your installed Pi CLI and authenticated model providers. It sends prompts, instructions, and vault excerpts to the selected provider after explicit first-use consent. Provider retention and training policies apply.

Obsibrain collects no telemetry. Copy Diagnostics creates a redacted report on
request and places it on your clipboard; it does not send it. The report leaves
your device only when you share it. See [Privacy](PRIVACY.md) for local storage,
network requests, and data handling.

## Access outside the current vault

Desktop features need the following external access:

- The v1 importer reads the external vault you select to analyze and import old content. It never changes that source vault.
- AI runs your local Pi and Obsidian CLI executables. Pi stores provider credentials and conversation history outside the vault. Obsibrain writes its bundled, guarded Pi extension to a private temporary directory and removes it on shutdown.

Migration sends no data over the network. AI uses the current vault only for its
note tools. Obsibrain does not copy or store model-provider credentials.

## Support and license

Contact support through [obsibrain.com](https://obsibrain.com). Report security
issues privately as described in [Security](SECURITY.md).

Copyright © Pierre Mouchan. All rights reserved. See [LICENSE](LICENSE) for the
existing proprietary terms and [obsibrain.com](https://obsibrain.com) for purchase
information. This repository distributes compiled releases; source remains private.
