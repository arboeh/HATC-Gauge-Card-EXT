# HATC Gauge Card EXT

## Installation

Got to HACS and add https://github.com/arboeh/hatc-gauge-card-ext to the custom repository and choose Lovelace frontend as category.

![Dépots personnalisé](https://github.com/tagcashdev/hatc-gauge-card/blob/main/img/installation.png)

Then press the button (+ Explore and download repositories), search for HATC Gauge Card EXT and install.
Enjoy!

## Description

EXTended, personalized card for lovelace which can be used as a card or element in a button-card for example.  
Added the option to measure negative values also and translated to english.  
Positive measured values ​​are displayed clockwise in the range from 0° to 360°, negative values ​​are displayed counterclockwise in the range from 360° to 0°. Zero point of the gauge is "north".  
Forked from [tagcashdevs hatc-gauge-card](https://github.com/tagcashdev/hatc-gauge-card).

#### Options
| Name | Type | Required | Default | Description | Options |
| ---- | ---- | ------ | ------- | ----------- | ------- |
| type | String | **Yes** | - | `custom:hatc-gauge-card-ext` | - |
| entity | String | **Yes** | - | `sensor.outside_temperature` | - |arboeh/hatc-gauge-card-ext
| [card](https://github.com/arboeh/hatc-gauge-card-ext/#card-options) | Object | No | NULL | Height of the card, [view example](https://github.com/arboeh/hatc-gauge-card-ext/#default) | px |
| [title](https://github.com/arboeh/hatc-gauge-card-ext/#title-options) | String/Object | No | \<ENTITY_ATTRIBUTE\>.friendly_name | Title of the card, [view example](https://github.com/arboeh/hatc-gauge-card-ext/#simple-card-title) | false, "", hide, String, Object, [view configuration](https://github.com/arboeh/hatc-gauge-card-ext/#title-options) |
| [gauge](https://github.com/arboeh/hatc-gauge-card-ext/#gauge-options) | Object | No | - | Gauge configuration | - |

#### Card Options
| Name | Type | Required | Default | Description | Options |
| ---- | ---- | ------ | ------- | ----------- | ------- |
| height | String | No | - | Height of card | px |


#### Title Options
| Name | Type | Required | Default | Description | Options |
| ---- | ---- | ------ | ------- | ----------- | ------- |
| name | String | No | - | Title of the card | false, String |
| text-align | String | No | left | Title alignment | left, center, right |
| font-size | String | No | 22px | Title font size | px, em |
| text-color | String | No | var(--secondary-text-color) | Color of the card title, note that severity allows you to change the color of the text automatically according to the colors chosen in the severity option | severity, red, #ff0000, rgb(255,0,0), var(--color) |
| icon | String | No | \<ENTITY_ATTRIBUTE\>.icon | Icon of the card title, note that severity allows you to change the icon automatically depending on the icons chosen in the severity option | false, mdi:xxx, severity |
| icon-color | String | No | white | Color of the card title icon, note that severity allows you to change the color of the text automatically according to the colors chosen in the severity option | severity, red, #ff0000, rgb(255,0,0), var(--color) |

#### Gauge Options
| Name | Type | Required | Default | Description | Options |
| ---- | ---- | ------ | ------- | ----------- | ------- |
| min_value | String/Integer | No | -100 | Allows you to modify the minimum value of the gauge and automatically adapt the position of the gauge | - |
| max_value | String/Integer | No | 100 | Allows you to modify the maximum value of the gauge and automatically adapt the position of the gauge | - |
| state | String | No | \<ENTITY\>.state | Allows you to modify the status value or hide the status in the gauge | false, String |
| text-color | String | No | black | Allows you to change the color of the text inside the gauge circle, note that severity allows you to change the color of the text automatically according to the colors chosen in the severity option | severity, red, #ff0000, rgb(255,0,0), var(--color) |
| font-size | String | No | 22px | Gauge state text size | px, em |
| unit_of_measurement | String | No | \<ENTITY_ATTRIBUTE\>.unit_of_measurement | Allows you to change the unit value or hide the unit in the gauge | false, String |
| icon | String | No | \<ENTITY_ATTRIBUTE\>.icon | Gauge icon, note that severity allows you to change the icon automatically depending on the icons chosen in the severity option | false, mdi:xxx, severity |
| icon-color | String | No | white | Color of the gauge icon, note that severity allows you to change the color of the text automatically according to the colors chosen in the severity option | severity, red, #ff0000, rgb(255,0,0), var(--color) |
| icon-size | String | No | 22px | Gauge icon size | px, em |
| [severity](https://github.com/arboeh/hatc-gauge-card-ext/#severity-options) | Object | No | - | Configuration severity | - |

#### Severity Options
| Name | Type | Required | Default | Description | Options |
| ---- | ---- | ------ | ------- | ----------- | ------- |
| color | String | No | - | Color to use | red, #ff0000, rgb(255,0,0), var(--color) |
| from | Integer | No | - | From | number |
| to | Integer | Optionnel | - | To | number |
| icon | Integer | Optionnel | - | Icon | mdi:xxx |

## Examples

#### Minimum

```yaml
type: custom:hatc-gauge-card
entity: sensor.temperature_outside
```
![Minimum](https://github.com/arboeh/hatc-gauge-card-ext/blob/main/img/minimum.png)

#### Default

```yaml
type: custom:hatc-gauge-card
entity: sensor.temperature_outside

card:
  height: 150px

title: Card title

gauge:
  min_value: -25
  max_value: 50 
  text-color: severity
  unit_of_measurement: false
  severity:
    - color: blue
    - color: yellow
      from: 20
      to: 22
    - color: orange
      from: 22
      to: 24
    - color: var(--red)
      from: 24
      to: 26
    - color: purple
      from: 26
      to: 28
    - color: purple
      icon: mdi:xxx
      from: 28
      to: 50
```

#### Simple card title

```yaml
title: Card title
```
![Simple card title](https://github.com/arboeh/hatc-gauge-card-ext/blob/main/img/titre-simple.png)

#### Title options

```yaml
title:
  name: Card title
  text-align: center
  font-size: 20px
  text-color: red
  icon-color: severity
  icon: severity
```
![Title options](https://github.com/arboeh/hatc-gauge-card-ext/blob/main/img/titre-options.png)


#### Hide card title

Solution n°1

```yaml
type: custom:hatc-gauge-card
entity: sensor.temperature_moyenne_hall_d_entree
title:
  name: false
  icon: false
```

Solution n°2

```yaml
type: custom:hatc-gauge-card
entity: sensor.temperature_moyenne_hall_d_entree
title: false
```
![Title options](https://github.com/arboeh/hatc-gauge-card-ext/blob/main/img/cacher-titre.png)


#### Gauge options

```yaml
gauge:
  min_value: -25
  max_value: 50 
  text-color: severity
  unit_of_measurement: false
  state: false
  icon: severity
  icon-size: 12px
  icon-color: white
  severity:
    - color: blue
    - color: yellow
      from: 20
      to: 22
    - color: orange
      from: 22
      to: 24
    - color: var(--red)
      from: 24
      to: 26
    - color: purple
      from: 26
      to: 28
    - color: purple
      icon: mdi:xxx
      from: 28
      to: 50
```
![Gauge Options](https://github.com/arboeh/hatc-gauge-card-ext/blob/main/img/gauge-options.png)

#### Severity options

```yaml
gauge:
  severity:
    - color: #0000FF
    - color: rgb(0,255,00)
      from: 20
      to: 22
    - color: orange
      from: 22
      to: 24
    - color: var(--red)
      from: 24
      to: 26
    - color: purple
      from: 26
      to: 28
    - color: purple
      icon: mdi:xxx
      from: 28
      to: 50
```
