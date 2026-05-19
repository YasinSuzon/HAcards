# Temperature & Humidity for indoor & outdoor
![Temperature and Humidity](https://raw.githubusercontent.com/YasinSuzon/HAcards/main/Photos/Temperature%20%26%20Humidity%20for%20indoor%20%26%20outdoor.png)

<details>
<summary>For Temperature</summary>

```yaml
type: custom:mod-card
card_mod:
  style: |
    ha-card {
      position: relative;
      overflow: hidden;
    }
card:
  type: vertical-stack
  cards:
    - type: entities
      theme: Graphite Auto
      card_mod:
        style: |
          ha-card {
            background: transparent !important;
            border: none !important;
            box-shadow: none !important;
            padding: 12px 16px !important;
            position: relative;
            z-index: 2;
          }
      entities:
        - entity: sensor.zhimi_rmb1_f34c_temperature
          type: custom:multiple-entity-row
          name: Temperature
          icon: mdi:home-thermometer-outline
          show_state: false
          entities:
            - entity: sensor.zhimi_rmb1_f34c_temperature
              name: false
            - entity: sensor.temp_sensor_temperature
              name: false
    - type: custom:apexcharts-card
      layout: minimal
      card_mod:
        style: |
          ha-card {
            position: absolute !important;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: transparent !important;
            border: none !important;
            box-shadow: none !important;
            opacity: 0.4;
            z-index: 1;
            pointer-events: none;
          }
      series:
        - entity: sensor.zhimi_rmb1_f34c_temperature
          type: area
          color: "#3498db"
          stroke_width: 1.5
          opacity: 0.25
          fill_raw: last
        - entity: sensor.temp_sensor_temperature
          type: area
          color: "#e67e22"
          stroke_width: 1.5
          opacity: 0.2
          fill_raw: last
      apex_config:
        chart:
          height: 100%
          sparkline:
            enabled: true
        legend:
          show: false
```
