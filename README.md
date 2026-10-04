# Wealth Log Book plugins

Community plugins for [Wealth Log Book Automation](https://wealthlogbook.com/#automation): **parser plugins** that read a bank's or broker's statements (PDF, CSV or Excel), and **general rule plugins** that sort transactions into income, expenses and categories.

Every plugin here is checked automatically before it's merged (format, required details, and a scan for personal data), and reviewed by hand. The catalogue the app and the website read is [`index.json`](index.json), rebuilt on every merge.

## Layout

```
<country>/<institution>/<statement-type>-parser.yaml    e.g. india/icici-bank/savings-account-parser.yaml
<country>/rules/<name>-rule.yaml                        e.g. india/rules/common-merchants-rule.yaml
global/rules/<name>-rule.yaml                           rules not tied to one country
```

Folder and file names come from the plugin's `library` details (lower case, words joined by hyphens).

## Using a plugin

1. Download the plugin's `.yaml` file.
2. In Wealth Log Book Automation, put it in your plugins folder (Settings → Plugins and database shows where).
3. Open it on the **Parsers** page and check the preview on your own statement before you rely on it.

Plugins are offered as-is: always check the results against your statements (see the [Terms](https://wealthlogbook.com/terms.html)).

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). In short: one plugin per pull request, with a `library` block, no personal data, and a higher `version` when you change a plugin. Missing your bank? Open a **Parser request** issue.

## Licence

The plugins are dedicated to the public domain under [CC0 1.0](LICENSE): anyone may use, change and share them, with no conditions. By contributing, you agree to release your plugin under CC0. Authors are credited in each plugin's `library.author`.
