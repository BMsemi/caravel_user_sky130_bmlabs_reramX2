# Analog routing with LibreLane NDR

This project uses LibreLane's supported non-default-rule configuration. It does
not patch `drt.tcl`, build a custom LibreLane image or modify a Nix store.

The rules live directly in `openlane/user_project_wrapper/config.json`:

- `NON_DEFAULT_RULES` defines widths and spacings;
- `DRT_ASSIGN_NDR` maps exact analog net-name regular expressions to rules.

The assignments preserve the previously documented groups:

| Rule | Nets |
|---|---|
| `NDR_ANALOG_SUPPLY` | `analog_io[19]`, `[20]`, `[21]`, `[22]`, `[23]`, `[25]`, `[26]`, `[27]` |
| `NDR_ANALOG_BIAS_SAFE` | `analog_io[24]` |
| `NDR_ANALOG_DC_BIAS_EXTRA_SAFE` | `analog_io[18]` |

Run the normal project command:

```bash
make user_project_wrapper
```

Review the detailed-routing log to confirm each regex matched its intended net,
then require routing DRC, Magic/KLayout DRC and LVS to pass. If the LibreLane
schema changes, update the project configuration and report deficiencies
upstream rather than modifying installed tool sources.
