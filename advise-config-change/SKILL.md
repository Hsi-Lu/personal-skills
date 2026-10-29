---
name: advise-config-change
description: Structures configuration change instructions to include pre-change status verification, change steps, and rollback instructions. Use whenever showing the user how to change a configuration, setting, environment variable, dotfile, service config, or system parameter.
---

# Advise Configuration Change

Whenever showing the user how to change a configuration, always include these three steps in order:

1. **Verify (Before)**: How to inspect the current value or state before making changes.
2. **Change**: How to apply the new setting (plus any required reload/restart and post-change check).
3. **Revert**: How to restore the original setting or default behavior (back up files first if editing critical configs).

Keep the length proportional to complexity—1–2 lines per step for simple flags, fuller steps for service configs.

## Example

**User**: How do I set git to rebase by default when pulling?

**1. Verify current setting**
```bash
git config --global --get pull.rebase
```

**2. Apply change**
```bash
git config --global pull.rebase true
```

**3. Revert**
```bash
git config --global --unset pull.rebase
```