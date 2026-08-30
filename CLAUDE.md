@AGENTS.md

## Notes for Claude

- Devices are described by declarative YAML in `custom_components/tuya_local/devices/`,
  not code. A device is matched to a config by comparing its live DPS to each
  config's dps ids/types. Authoritative format guide:
  `custom_components/tuya_local/devices/README.md`.
- When a config change causes match ambiguity, use the `util/` matching scripts
  (exposed as `uv run best_match`, `all_matches`, `match_against`, `duplicates`)
  to check which config a given device's dps resolves to and whether two configs
  now collide.
- `tests/test_device_config.py` enforces structural rules on every device YAML
  (no unused/duplicate dps, valid ranges, matchable). A new device almost always
  needs no new Python test — the config test covers it.
