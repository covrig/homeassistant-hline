# Horizontal line state card for [Home Assistant](https://home-assistant.io)
Used to separate entities in a Home Assistant group 

<img align="left" src="https://i.imgur.com/mQiMmGg.jpg" height="350">

***
***
## Features
* Highly customizable: widthm, thickness, borders, images, color, dashes, double lines etc.
* More than one can be added to the interface.
* Disabled more-info card.
***
KNOWN PROBLEMS: Not all options exposed in the `customize` section.
***
***
## Installation
* Download `/www/custom_ui/state-card-hline.html` to `<your-hass-configuration-dir>/www/custom_ui/` (create the folder structure if you don't have it - mind the permissions)
* Add it to your `configuration.yaml`:
```yaml
frontend:
  extra_html_url:
    - /local/custom_ui/state-card-hline.html
```
* Create one or more sensors, binary_sensor(s), input_text(s) etc. in your `configuration.yaml`. 
If you plan to use only one design for you horizontal line just create one sensor and use it in the groups you want.
```yaml
sensor:
  - platform: template
    sensors:
      hline_1:
        value_template: hline
      hline_2:
        value_template: hline
```
* Add your sensor to a group between the entities you would like to split E.g.:
```yaml
group:
  your_group:
    name: ' '   > in this format the chart will not have a name above (recommeded)
    entities:
      - sensor.1
      - sensor.hline_1
      - sensor.2   
      - sensor.hline_2
```
* Convert your newly created sensor (or an existing one that you don't use) to a horizontal line in the `customize` section or your `customize.yaml` file:

```yaml
  customize:
    sensor.hline_1:
      custom_ui_state_card: state-card-hline
    sensor.hline_2:
      custom_ui_state_card: state-card-hline
 ```
 or in the `customize_glob.yaml` file:
 ```
     sensor.hline_*:
      custom_ui_state_card: state-card-hline
 ```
 * Customize your horizontal line in the `customize` section or the `customize.yaml` file:

 ```yaml
     sensor.hline_1:
      custom_ui_state_card: state-card-hline
      config:
        width: 90 --> in percents
        height: 0 --> in pixels, adds to bordertop
        backgroundcolor: white
        bordertop: '1px solid black'
    sensor.hline_2:
      custom_ui_state_card: state-card-hline
      config:
        width: 90 --> in percents
        height: 0 --> in pixels, adds to bordertop
        backgroundcolor: white
        bordertop: '1px dashed red'
    sensor.hline_3:
      custom_ui_state_card: state-card-hline
      config:
        width: 65 --> in percents
        height: 0 --> in pixels, adds to bordertop
        backgroundcolor: white
        bordertop: '2px double green'
    sensor.hline_4:
      custom_ui_state_card: state-card-hline
      config:
        width: 85 --> in percents
        height: 2 --> in pixels, adds to bordertop
        backgroundimage: linear-gradient(to right, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.75), rgba(0, 0, 0, 0))
 ```
 ```
 default values:
       config:
        width: 85
        height: 0
        backgroundcolor: white
        bordertop: '1px solid black'
        backgroundimage: none
 ```
## Changelog
```
Version 20180208:
Start
```

Some ideas for customizing:
* https://codepen.io/ibrahimjabbari/pen/ozinB
* https://css-tricks.com/examples/hrs/
