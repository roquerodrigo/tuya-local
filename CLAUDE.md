@AGENTS.md

## Notes for Claude

- This is a **personal fork** of `make-all/tuya-local` (`origin` =
  `roquerodrigo/tuya-local`, `upstream` = `make-all/tuya-local`). Unlike upstream,
  which ships thousands of device configs, this fork intentionally keeps **only
  the owner's own devices** in `custom_components/tuya_local/devices/` (currently
  5 YAML files). Do not re-import the full upstream catalog. `DEVICES.md` and
  `ACKNOWLEDGEMENTS.md` still carry upstream's full listing and are out of sync
  with what's actually configured here — that's expected, don't "fix" them.
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
- The `hacs-validate.yml` workflow assumes the upstream repo; per AGENTS.md it
  can be ignored when not running from `make-all/tuya-local`.
