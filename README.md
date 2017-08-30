# homebridge-hive-motion

This [HomeBridge](https://github.com/nfarina/homebridge) Plugin adds support for the Hive Active Heating motion sensors to be controlled in the Home app in iOS and via Siri.

This is heavily based on the work by Mark Wade in the [homebridge-hive plugin](https://github.com/mark-wade/homebridge-hive)

## Installation

### 1. Install HomeBridge

This is a plugin for HomeBridge. In order to use this, you will need to install HomeBridge. You will need a computer which is always turned on. Personally, I use a [Raspberry Pi](https://www.raspberrypi.org) but this may not be for the faint-hearted. Any Windows machine or Mac will do fine.

1. Install [Node.JS](https://nodejs.org) - whatever version is currently "Recommended for most users" should be fine, but this was developed on 6.9.
2. Install [HomeBridge](https://github.com/nfarina/homebridge) by running the commands provided in their documentation (you don't need to download anything - you're using Node's package manager)
3. Create a config.json file inside your home directory (so on macOS and Linux the path will be `~/.homebridge/config.json`) using the [sample file](https://github.com/nfarina/homebridge/blob/master/config-sample.json) provided by HomeBridge.
4. Start HomeBridge by running the `homebridge` command
5. Add HomeBridge to your iOS device in the Home app using the key provided.

### 2. Install this plugin

Run this command (you don't need to download anything - you're using Node's package manager)

```
npm install -g homebridge-hive-motion
```

### 3. Configure HomeBridge

In your `config.json` file, add this accessory providing the username and password you use to log into https://my.hivehome.com

```
    "accessories": [
        {
            "accessory": "HiveMotionSensor",
            "name": "Dining Room",
            "username": "you@example.com",
            "password": "123456789"
        }
    ],
```

You need an accessory entry for each motion sensor. The name must match the hive motion sensor name.

Then restart homebridge.

## Known Issues

* The state of the motion sensors is only checked whenever the 'Home' app is accessed, Siri is used to enquire ('Is there movement in my home?'), or the sensor appears as a favourite. Hence it is pretty much useless as a trigger. It would be possible to add polling to this plugin but that is a little anti-social and may cause problems for the Hive web api.
* If you go into the Details in the Home app, you will see a blank space next to Serial Number. This is because the Hive API doesn't expose this information but again, HomeKit seems to require it.

