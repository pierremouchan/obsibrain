# Privacy

Obsibrain operates primarily on files inside the user's Obsidian vault. It does not include an
analytics or advertising SDK.

## Network requests

The plugin makes these requests when the related feature runs:

- License validation sends the entered purchase email and license key, or the stored license
  credential, to `https://www.obsibrain.com/api/validate-license`.
- The Paste key action reads clipboard text only after a tap and fills the license field.
  Clipboard text is sent only if the user activates the license.
- Completing onboarding sends the stored purchase email to
  `https://www.obsibrain.com/api/onboarding-finish`.
- Update checks request public release metadata from the GitHub API for `pierremouchan/obsibrain`.
- Automatic or user-triggered update installation downloads `main.js`, `manifest.json`, and
  `styles.css` from the matching public GitHub release.
- The optional Obsibrain AI (Alpha) desktop panel launches the user's local Pi CLI. Pi sends chat prompts,
  instructions, and content returned by allowlisted read-only Obsidian CLI tools to the selected
  model provider. Available providers and models depend on the user's Pi authentication and
  configuration. Provider retention, training, and account policies apply. The panel sends nothing
  until the user accepts a first-use disclosure in that vault.

Obsibrain stages, validates, backs up, and installs these release assets locally.
External links open only after a user action.

The desktop v1 migration wizard reads a user-selected external vault only after explicit action.
Analysis and import send no migration data over the network. Analysis keeps the absolute source path
and session state in memory only. Import writes converted files and one local report inside the
current target vault. Reports contain relative note paths, conversion codes, warnings, and counts.
Paths can contain names, email addresses, or other identifiers present in filenames. Reports exclude
note bodies, absolute paths, credentials, binary data, and raw stacks.
The Copy support summary action places a redacted summary without note names on the clipboard.

## Diagnostics

Obsibrain collects no telemetry. Copy Diagnostics builds a support report on request and copies it to
the clipboard. The report contains plugin and Obsidian versions, platform, license validity, settings
state, and the last 200 console entries from the current session. Note names, vault paths, quoted
text, and executable paths are removed before an entry is stored. The report leaves the device only
when the user pastes it.

## Data stored locally

The plugin stores its settings through Obsidian and keeps license validation state, the purchase
email, and language preference in the Obsidian window's local storage. It also reads and modifies
managed vault files to provide commands, native task actions, archiving, templates, and integrity checks.
Future v2 data changes use a local schema runner. Release tracking and first-run onboarding use separate settings.
The external v1 importer stays separate from that schema runner and does not persist its source path.

The Obsibrain AI (Alpha) desktop panel stores the provider-qualified model, thinking level, consent version,
executable paths, vault instructions, and Pi session identifier in Obsidian plugin settings. The
session identifier keeps one conversation available across Obsidian sessions until the user starts
a new chat. Pi stores provider credentials and session history outside Obsibrain according to the
user's Pi configuration. Obsibrain does not copy or store provider credentials. The agent can
receive vault content only after it invokes an allowlisted Obsidian CLI read tool. The panel cannot
change vault content.

Users can remove the plugin and its local settings through Obsidian. License-related local storage
can be cleared by removing the corresponding site/app data. Server-side privacy or deletion
requests should be sent through [obsibrain.com](https://www.obsibrain.com).
