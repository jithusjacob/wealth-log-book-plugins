# Contributing a plugin

Thank you for helping other people read their statements.

## What's accepted

- **Parser plugins** for a bank's or broker's statement (PDF, CSV or Excel).
- **General rule plugins**: category rules that make sense for everyone in a country (for example, common merchants).
- **Never** personal rules: tags (emergency fund, goals, accounts) and rules for your own merchants or people stay on your computer.
- **Never** personal data: no account or card numbers, IBANs, names, email addresses, phone numbers or ID numbers (PAN, SSN, NI number…), not even in comments. Use regex patterns (`\d+`, `\S+`) instead of real values.
- **Never** statements or sample files: only `.yaml` plugins (and `.md` notes) belong here.

## The `library` block

Every plugin here has one. It's described in the app's plugin format (`PLUGIN_FORMAT.md` and `RULE_FORMAT.md` in your plugins folder).

```yaml
library:
  country: India                    # English name ("Global" for rules not tied to one country)
  institution: ICICI Bank           # parsers only
  statementType: Savings account    # parsers only
  emailDomains: ["@icicibank.com"]  # parsers, optional: senders of the statement emails
  author: { name: Your Name, link: https://github.com/you }  # link optional
  maintainer: your-github-username
  updated: 2026-10-04
```

The file goes where its details say: `india/icici-bank/savings-account-parser.yaml` for the example above, or `<country>/rules/<name>-rule.yaml` for a rule plugin.

## Steps

1. Make and test the plugin in Wealth Log Book Automation on your own statements.
2. Add the `library` block, and check the file once more for anything personal.
3. Optional: run the checker yourself (Linux x86_64):
   ```sh
   curl -LO https://wealthlogbook.com/tools/wlb-plugin-check-linux-x86_64
   chmod +x wlb-plugin-check-linux-x86_64
   ./wlb-plugin-check-linux-x86_64 file my-bank-parser.yaml
   ```
4. Open a pull request adding the file in the right folder. One plugin per pull request.
5. Changing an existing plugin? Raise its `version` and update `library.updated`. Keep the original author; add yourself as maintainer if you'll look after it.

Checks run on every pull request and must pass. A maintainer then reviews it. When it's merged, `index.json` is rebuilt and the plugin appears in the catalogue.

## Licence

By contributing, you confirm the plugin contains no personal data, that you have the right to share it, and that it's released under [CC0 1.0](LICENSE).
