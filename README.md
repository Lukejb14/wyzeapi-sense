# Home Assistant - Wyze Bulb, Switch, Sensor and Lock Integration

This is a custom component to allow control of Wyze Bulbs, Switches, Sensors, and Locks in Home Assistant using the unofficial Wyze API. Please note this mimics the Wyze app and therefore Wyze may cut off access at anytime.

### Highlights of what **WyzeApi** can do

* Control Wyze Bulbs as lights through HA
* Control Wyze Switches as switches through HA
* View Wyze Sensors as binary_sensor through HA
* View Wyze Lock Status and Door Status as lock through HA
	* ***Note:* Currently you can only view the lock status or door status. Lock and Unlock does not work!**

### Potential Downsides

* This is an unofficial implementation of the api and therefore may be disabled or broken at anytime by WyzeLabs
* I only have light bulbs and no switches so they are not tested directly by me. An update may break them without my knowledge. **Please use the betas as they become available if you have switches to help me find bugs prior to release**
* ***It requires two factor authentication to be disabled on your account***

## Support
If you like what I have done here and want to help I would recommend that you firstly look into supporting Home Assistant. You can do this by purchasing some swag from their [store](https://teespring.com/stores/home-assistant-store) or paying for a Nabu Casa subscription. None of this could happen without them.

After you have done that if you feel like my work has been valuable to you I welcome your support through BuyMeACoffee.

<a href="https://www.buymeacoffee.com/joshmulliken" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/default-blue.png" alt="Buy Me A Coffee" style="height: 51px !important;width: 217px !important;" ></a>

## Installation (HACS) - Highly Recommended

1. Have HACS installed, this will allow you to easily update
2. Add [https://github.com/JoshuaMulliken/ha-wyzeapi](https://github.com/JoshuaMulliken/ha-wyzebulb) as a custom repository as Type: Integration
3. Click install under "Wyze Bulb and Switch Api Integration" in the Integration tab
4. Restart HA

## Installation (Manual)

1. Download this repository as a ZIP (green button, top right) and unzip the archive
2. Copy `/custom_components/wyzeapi` to your `<config_dir>/` directory
   * On Hassio the final location will be `/config/custom_components/wyzeapi`
   * On Hassbian the final location will be `/home/homeassistant/.homeassistant/custom_components/wyzeapi`
3. Restart HA

## Configuration

Add the following to your configuration file. ***Note: This has changed recently. Check your configuration!***

```yaml
wyzeapi:
  username: <email for wyze>
  password: <password for wyze>
```
You can exclude any of the devices.

```yaml
wyzeapi:
  username: <email for wyze>
  password: <password for wyze>
  sensors: false
  light: false
  switch: false
  lock: false
```
## Usage

* Restart HA
* Entities will show up as `light.<friendly name>`, `switch.<friendly name>`, `binary_sensor.<friendly name>` or `lock.<friendly name>` for example (`light.livingroom_lamp`).
* Instructions for interacting with lights can be found here: https://www.home-assistant.io/integrations/light/
	* Switches: https://www.home-assistant.io/integrations/switch/
	* Locks: (These devices only work as sensors right now. There is a technical limitation preventing control via the cloud api)

## More information and Help

If you would like more information then please look at the [wiki](https://github.com/JoshuaMulliken/ha-wyzeapi/wiki)!

## Reporting an Issue

1. Setup your logger to print debug messages for this component by adding this to your `configuration.yaml`:
    ```yaml
    logger:
      default: warning
      logs:
        custom_components.wyzeapi: debug
    ```
2. Restart HA
3. Verify you're still having the issue
4. File an issue in this Github Repository

