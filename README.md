# WIT HA Lovelace Card

Custom Lovelace card for Home Assistant to visualize RV leveling based on WIT tilt sensor data (pitch/roll), including corner raise guidance and key telemetry values.

## Status

This is the initial MVP (`0.1.0`) focused on visualization and editor-based configuration.

Planned next step: dedicated Home Assistant integration for WT901WIFI/WIT data source.

## Features (MVP)

- RV top-view visualization similar to your current dashboard style
- Frontend configuration via Lovelace card editor (no mandatory YAML mapping)
- Configurable entities:
  - pitch
  - roll
  - temperature
  - battery SoC
- Configurable geometry:
  - wheelbase
  - front track
  - rear track
- Configurable display behavior:
  - max tilt range for center dot
  - level tolerance
  - text size mode (`auto`, `small`, `medium`, `large`)
  - optional temperature/battery/corner labels
- Orientation correction options:
  - swap X/Y
  - invert pitch
  - invert roll
- Click on values opens Home Assistant more-info
- German/English UI (German for `de*`, English for all other locales)

## Installation (HACS)

1. Open `HACS`.
2. Open menu (top-right, 3 dots) -> `Custom repositories`.
3. Add repository URL:
   - `https://github.com/othorg/wit-ha-lovelace-card`
4. Category: `Dashboard`.
5. Install **WIT HA Lovelace Card**.
6. Reload browser tab (or restart Home Assistant frontend once).
7. Add card in dashboard.

## Manual resource (optional)

If needed, add manually:

- URL: `/hacsfiles/wit-ha-lovelace-card/wit-ha-lovelace-card.js`
- Type: `module`

## Card type

`custom:wit-ha-lovelace-card`

## Example YAML (optional)

```yaml
type: custom:wit-ha-lovelace-card
title: Flair 920 - Wasserwaage
entities:
  pitch: sensor.easylevelrv_neigung_x
  roll: sensor.easylevelrv_neigung_y
  temperature: sensor.easylevelrv_temperatur
  battery_soc: sensor.easylevelrv_batterie
geometry:
  wheelbase_mm: 2000
  track_front_mm: 1723
  track_rear_mm: 1661
display:
  max_tilt_deg: 5
  level_tolerance_cm: 0.1
  text_size_mode: auto
orientation:
  swap_axes: false
  invert_pitch: false
  invert_roll: false
```

## Development

Run tests:

```bash
npm test
```

## Assets

- Base image: `assets/rv_top_flair.png`
- Icon: `assets/wit-icon.svg`

Mirrored files for HACS resource use are available in `dist/`.
