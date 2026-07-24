# ConnectWunder for Codex

The official ConnectWunder plugin lets Codex work with the ConnectWunder workspace you authorize: people, companies, boards, documents, meetings, activity, and calendar workflows.

This is a distribution repository. It contains only the Codex marketplace package and setup documentation; it does **not** contain the private ConnectWunder application source code, deployment configuration, or credentials.

## Requirements

- An individual ChatGPT account with Codex access (ChatGPT Pro is supported).
- A ConnectWunder account with access to at least one workspace.
- The Codex command-line binary supplied with the ChatGPT desktop app.

## Install

In Terminal, run:

```bash
/Applications/ChatGPT.app/Contents/Resources/codex plugin marketplace add SebastianMaierOfficial/connectwunder-codex-plugin
/Applications/ChatGPT.app/Contents/Resources/codex plugin add connectwunder@connectwunder-official
```

If you use the command often, add this temporary shortcut for the current Terminal window:

```bash
alias codex='/Applications/ChatGPT.app/Contents/Resources/codex'
```

Then the same setup is:

```bash
codex plugin marketplace add SebastianMaierOfficial/connectwunder-codex-plugin
codex plugin add connectwunder@connectwunder-official
```

## Activate ConnectWunder

1. Open the ChatGPT desktop app and create a new Codex task.
2. Select or mention **ConnectWunder** when needed.
3. On first use, complete the ConnectWunder OAuth sign-in and select the intended workspace.
4. Start with this prompt:

   > Give me a short overview of my ConnectWunder workspace and its enabled modules.

The plugin’s onboarding skill uses a read-first approach. It will not create, update, move, or delete workspace data unless you explicitly request it.

## Example prompts

- “Summarize the most important activity from the last seven days.”
- “Find people and companies related to the Acme project.”
- “Show open board items that need my attention.”
- “Prepare a follow-up checklist from my next meeting.”
- “Create a board item from these agreed next steps: …”
- “Build and publish a secure lead form that creates people and items in my sales board.”
- “Read this spreadsheet, structure it as a ConnectWunder board, and build a website that stays updated from its public JSON feed.”
- “Interview me and create a living Brand OS from my websites, logos, product screens, and visual inspiration.”

## Update or reinstall

When a new plugin version is released, refresh the marketplace and reinstall the plugin:

```bash
/Applications/ChatGPT.app/Contents/Resources/codex plugin marketplace upgrade connectwunder-official
/Applications/ChatGPT.app/Contents/Resources/codex plugin remove connectwunder@connectwunder-official
/Applications/ChatGPT.app/Contents/Resources/codex plugin add connectwunder@connectwunder-official
```

If an earlier installation used a local marketplace, remove that old installation first, then use the install commands above.

```bash
/Applications/ChatGPT.app/Contents/Resources/codex plugin remove connectwunder@connectwunder-official
/Applications/ChatGPT.app/Contents/Resources/codex plugin marketplace remove connectwunder-official
```

Then run the commands in [Install](#install) again. This matters because the previous local marketplace used the same marketplace name, `connectwunder-official`.

## Privacy and access

Every person authorizes ConnectWunder separately through OAuth. The plugin can access only the ConnectWunder workspace and permissions granted to that person. Never share a personal API key or OAuth session with a teammate.

- Website: <https://app.connectwunder.com>
- Privacy policy: <https://www.yonju.de/privacy>
- Terms: <https://app.connectwunder.com/legal/contracts/terms>

## Support

Open an issue in this repository with the Codex version, the plugin version, and a redacted description of the problem. Do not include API keys, OAuth tokens, or private workspace data.

## License

No open-source license has been selected for this distribution package yet. Public availability does not grant permission to reuse the ConnectWunder name, logo, or service outside use of this plugin. Contact ConnectWunder for licensing or partnership questions.
