# slider-entity-row

Add a slider to rows in lovelace [entities](https://www.home-assistant.io/lovelace/entities/) cards.

## Installing

[![hacs_badge](https://img.shields.io/badge/HACS-Default-orange.svg)](https://github.com/custom-components/hacs)

Install using HACS or [see this guide](https://github.com/thomasloven/hass-config/wiki/Lovelace-Plugins).

## Quick Start

Add this to an [entities](https://www.home-assistant.io/lovelace/entities/) card:

```yaml
type: entities
entities:
  - light.bed_light
  - type: custom:slider-entity-row
    entity: light.kitchen_lights
```

![slider-entity-row](https://user-images.githubusercontent.com/1299821/59467898-15b16600-8e31-11e9-9924-53b108572d3a.png)

## Usage

`entity` can be an entity in one of the following domains:

- `light` - set brightness
- `media_player` - set volume
- `climate` - set temperature
- `cover` - set position
- `fan` - set speed (assumes first setting is `off`)
- `input_number` - set value (only if `mode: slider`)
- `input_select` - select option
- `number` - set value

If you want to control more than one entity with the same slider, use [light group](https://www.home-assistant.io/integrations/light.group/), [cover group](https://www.home-assistant.io/integrations/cover.group/) or a custom made [template entity](https://www.home-assistant.io/integrations/#search/template).

![domains](https://user-images.githubusercontent.com/1299821/59467899-1813c000-8e31-11e9-8abd-34c887a7db2a.png)

Available options:

| Option       | Values         | Description                                                                                                                               | default |
| ------------ | -------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | ------- |
| `min`        | number         | Minimum value of slider                                                                                                                   |         |
| `max`        | number         | Maximum value of slider                                                                                                                   |         |
| `step`       | number         | Step size of slider selection                                                                                                             |         |
| `toggle`     | `true`/`false` | Show a toggle or mute button if possible                                                                                                  | `false` |
| `hide_state` | `true`/`false` | `true`: Do not display the current state <br>`false`: Always display current state - even when the card is too narrow for it to be usable | none    |
| `grow`       | `true`/`false` | Make the slider as wide as possible (which is really just a little bit wider)                                                             | `false` |
| `full_row`   | `true`/`false` | Hide the icon and name and stretch slider to full width                                                                                   | `false` |
| `attribute`  | (see below)    | Which attribute the slider should control                                                                                                |         |

![options](https://user-images.githubusercontent.com/1299821/59467902-19dd8380-8e31-11e9-9173-97c9b6be3179.png)

<details><summary>YAML code for screenshot above</summary>

```yaml
type: entities
title: Options
entities:
  - type: custom:slider-entity-row
    entity: light.bed_light
    name: Default
  - type: custom:slider-entity-row
    entity: light.bed_light
    name: toggle
    toggle: true
  - type: custom:slider-entity-row
    entity: light.bed_light
    name: hide_state
    hide_state: true
  - type: custom:slider-entity-row
    entity: light.ceiling_lights
    name: hide_when_off
    hide_when_off: true
  - type: custom:slider-entity-row
    entity: light.ceiling_lights
    name: hide_when_off + toggle
    hide_when_off: true
    toggle: true
  - type: section
    label: full_row
  - type: custom:slider-entity-row
    entity: light.bed_light
    name: hide_state
    full_row: true
```

</details>

### Attribute

Currently, the following attribute settings are supported.

**For `light` domain:**

- `brightness_pct` - default
- `brightness`
- `color_temp`
- `hue`
- `saturation`
- `red`
- `green`
- `blue`
- `effect`
- `white_value` - deprecated
- `white` - for RGBW lights only
- `cold_white` - for RGBWW lights only
- `warm_white` - for RGBWW lights only

**For `cover` domain:**

- `position` - default
- `tilt`

---

<a href="https://www.buymeacoffee.com/uqD6KHCdJ" target="_blank"><img src="https://www.buymeacoffee.com/assets/img/custom_images/white_img.png" alt="Buy Me A Coffee" style="height: auto !important;width: auto !important;" ></a>
