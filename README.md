[![hacs_badge](https://img.shields.io/badge/HACS-Default-41BDF5.svg)](https://github.com/hacs/integration)
[![hacs_badge](https://img.shields.io/badge/HACS-Custom-41BDF5.svg)](https://github.com/hacs/integration)

[![Open your Home Assistant instance and open a repository inside the Home Assistant Community Store.](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=Kartax&repository=home-assistant-binance&category=integration)

![Binance Logo](images/binance_logo.png)

# Binance Integration for Home Assistant
A Home Assistant Integration for the cryptocurrency trading platform [Binance](https://www.binance.com/en).

Features:
 - [x] pull prices of a configurable list of currency pairs (e.g. BTCUSDT, XRPBTC...)
 - [x] additional attributes for each currency pair (priceChange, highPrice, lowPrice, volume, ...)
 - [ ] support configuration via the UI
 - [ ]  fetch personal account balance over secured api

![screenshot_2](images/screenshot_2.png) ![screenshot_1](images/screenshot_1.png) 


### Installation
I recommend to install this integration via HACS. Simply search for it\
or manually add this repository by using the "three-dots-menu" at the top right in HACS.


### Configuration
Configure the sensor(s) in ``configuration.yaml``. 
```
- platform: binance
  symbols:
    - BTCUSDT
    - ETHUSDT
- platform: template
  sensors:
    cena_btc:
      value_template: '{{ (states("sensor.binance_ticker_btcusdt")) | round(0)}}'
      friendly_name: 'BTCUSDt'
      unit_of_measurement: 'USD'
      device_class: monetary
      icon_template: mdi:currency-btc
    cena_eth:
      value_template: '{{ (states("sensor.binance_ticker_ethusdt")) | round(0)}}'
      friendly_name: 'ETHUSDt'
      unit_of_measurement: 'USD'
      device_class: monetary
      icon_template: mdi:currency-eth
```
