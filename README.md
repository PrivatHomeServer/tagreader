# Tag Reader for Home Assistant

The tag reader is a simple to build/use NFC tag reader, specially created for [Home Assistant](https://www.home-assistant.io). It is using a Wemos D1 and the PN532 NFC module. The firmware is built using [ESPhome](https://www.esphome.io).

> I am selling a pre-built version, a DIY version (assembly required) or just the case (use with own components). Check it out on [my website](https://adonno.com/product/tag-reader/).

![Photos of the final product](https://raw.githubusercontent.com/adonno/tagreader/master/docs/cases.jpg)

## Building the tag reader

To build your own tag reader, you need the following components:

 - ESP8266 D1 Mini [get yours here](https://s.click.aliexpress.com/e/_d8l72oB)
 - PN532 NFC Reader [get yours here](https://s.click.aliexpress.com/e/_dZNORIJ)
 - WS2812 [get yours here](https://s.click.aliexpress.com/e/_d82GRqr)
 - Buzzer [get yours here](https://s.click.aliexpress.com/e/_dZ5F5yj)

The 3D models for the case are [here](https://github.com/adonno/tagreader/tree/master/STLs).

### Connecting the components
![Photo of schematics](picture.jpg)

Connecting the components is fairly easy, but it does require soldering. You will need the following:
- Solder
- Soldering iron with a fairly thin tip
- About 40cm of thin wire, in, preferably, at least 6 different colors.



To flash the reader firmware to your D1 Mini you have two options. You can load up the [tagreader.yaml](https://github.com/adonno/tagreader/blob/master/tagreader.yaml) in ESPHome and flash it from there, or you can use something like [NodeMCU PyFlasher](https://github.com/marcelstoer/nodemcu-pyflasher). If you're new to ESPHome, we recommend that you use the [ESPHome Home Assistant add-on](https://esphome.io/guides/getting_started_hassio.html).

![Open Case](https://raw.githubusercontent.com/adonno/tagreader/master/docs/open-case.jpg)

## Configuring for use with Home Assistant

If the tag reader is unable to connect to a wifi network, it will start a WiFi access point with a captive portal to allow you to enter your WiFi credentials.

The tag reader will be automatically found by Home Assistant once the tag reader is connected to the same network. You can follow the instructions in the UI to set it up.

A custom component is required for Home Assistant at this time to link the tag reader to the tag integration in Home Assistant. Copy [this file](https://raw.githubusercontent.com/adonno/tagreader/master/custom_components/esphome_tag.py) to `<config>/custom_components/esphome_tag.py` and add `esphome_tag:` to your `configuration.yaml` file.

## Usage

Each tag that is scanned will result in a `tag_scanned` event in Home Assistant. You can manage your tags and automate them in the Home Assistant UI under config -> tags.

![Screenshot of the Home Assistant tag UI](https://raw.githubusercontent.com/adonno/tagreader/master/docs/tag-ui.gif)

## Contributing

TODO
