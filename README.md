# agp-test-maven-properties

Test repository for [GUIDE-2167](https://sonatype.atlassian.net/browse/GUIDE-2167): verifies AGP correctly handles dependencies whose versions are controlled by Maven properties.

## What this tests

| Property | Current | Expected AGP behavior |
|---|---|---|
| `junit.version` | 4.13.2 (latest 4.x) | Downgrade blocked — should report **"Update skipped"** |
| `slf4j.version` | 1.7.36 | Upgradeable to 2.x — should **succeed** |
| `commons-lang3.version` | 3.12.0 | Upgradeable to 3.14+ — should **succeed** |

## Expected results after fix

- Property-based updates that can't proceed show "Update skipped" (not the old "Update failed - changes reverted")
- Valid upgrades through properties succeed normally
- Mixed groups (some skip, some succeed) report correctly
