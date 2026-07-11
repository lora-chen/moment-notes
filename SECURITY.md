# Security And Publishing Notes

`moment-notes` is intended to be a public Codex skill repository.

Do not commit:

- API keys, GitHub tokens, Codex `auth.json`, or environment snapshots
- `KINGSOFT_DOCS_TOKEN` or any WPS/KDocs credential
- private handoff bundles such as `handoff_*`
- private discussion logs, local product notes, or unreviewed prompt drafts
- raw user images, private test sets, or bad-case screenshots unless they are explicitly public-safe

Before pushing:

```bash
git status --short
rg -n "TOKEN|SECRET|KEY|auth\\.json|env_vars|KINGSOFT|gho_" .
```

Only public skill files should be committed here.
