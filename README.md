# homebridge-homeconnect

[![NPM](https://nodei.co/npm/homebridge-homeconnect.png)](https://nodei.co/npm/homebridge-homeconnect/)

Home Connect home appliances plugin for [Homebridge](https://github.com/nfarina/homebridge).

[Home Connect](https://www.home-connect.com), [Bosch](https://www.bosch-home.com/), [Siemens](https://www.siemens-home.bsh-group.com/), [Gaggenau](https://www.gaggenau.com/), [NEFF](https://www.neff-home.com/), and [Thermador](https://www.thermador.com/) are trademarks of [BSH Home Appliances](https://www.bsh-group.com).

## Installation

1. Connect your home appliances with Home Connect:
   1. Install Home Connect from the Apple App Store for your country (e.g. [UK](https://itunes.apple.com/gb/app/home-connect-app/id901397789) or [USA](https://itunes.apple.com/us/app/home-connect-america/id1134525430)).
   1. Create an account using your email address, click on the validation link in the email that will be received, and then return to the app and login.
   1. Connect the appliances to your home network, either via the app or using Wi-Fi Protected Setup (WPS).
   1. Connect the appliances to the app (by following the installation guide provided with the appliance).
1. Obtain a Home Connect application *Client ID*:
   1. Sign-up for a free [Home Connect Developer Program](https://developer.home-connect.com/user/register) account and login.
   1. [Register a new application](https://developer.home-connect.com/applications/add), ensuring that the *OAuth Flow* is set to *Device Flow*, and the *Home Connect User Account* is the same as the email address that was used within the Home Connect app.
   1. Save the displayed *Client ID* to include in the Homebridge `config.json` file.
1. Install this plugin using: `npm install -g homebridge-homeconnect`
1. Edit `config.json` and add the HomeConnect platform (see example below).
1. Run [Homebridge](https://github.com/nfarina/homebridge).
1. The Homebridge log output will include an authorisation URL. Copy the listed URL into a web browser and login to your Home Connect account. (The authorisation URL can also be found in the [homebridge-config-ui-x](https://github.com/oznu/homebridge-config-ui-x) graphical settings editor.)
 
### Example `config.json`
```JSON
{
    "platforms":
    [{
        "platform":     "HomeConnect",
        "clientid":     "0123456789ABCDEF0123456789ABCDEF0123456789ABCDEF0123456789ABCDEF"
    }]
}
```
The `clientid` should be set to the *Client ID* obtained from the [Home Connect Developer Program](https://developer.home-connect.com/applications) for the created *Device Flow* application.

For more advanced options refer to [Customising Appliance Programs](https://github.com/thoukydides/homebridge-homeconnect/wiki/Programs) and [`config.json`](https://github.com/thoukydides/homebridge-homeconnect/wiki/config.json).

The easiest way to configure this plugin is via the [homebridge-config-ui-x](https://github.com/oznu/homebridge-config-ui-x) (version 4.8.1 or later) graphical settings editor. This plugin dynamically updates its configuration schema with the appropriate options for the connected appliances.

## Appliance Support

The functionality supported by this plugin with different appliances types is described in:
* [Supported Home Connect Functionality](https://github.com/thoukydides/homebridge-homeconnect/wiki/Functionality)
* [HomeKit Services and Characteristics](https://github.com/thoukydides/homebridge-homeconnect/wiki/HomeKit-Mapping)
* [If This Then That (IFTTT) Comparison](https://github.com/thoukydides/homebridge-homeconnect/wiki/IFTTT)

Support for Hood appliances is currently experimental. Please provide feedback (whether good or bad) to [issue #2](https://github.com/thoukydides/homebridge-homeconnect/issues/2).

Oven appliances cannot be controlled due to the required [Home Connect Authorisation Scopes](https://github.com/thoukydides/homebridge-homeconnect/wiki/Scopes) not being granted. However, they can be switched on and off, and their operation monitored.

This plugin has only been tested by the developer with a Siemens [Dishwasher](https://www.siemens-home.bsh-group.com/uk/mysiemens/products/0004436388) (SN678D06TG/53), [Hob](https://www.siemens-home.bsh-group.com/uk/mysiemens/products/0004436379) (EX677LYV1E/06), and [Oven](https://www.siemens-home.bsh-group.com/uk/mysiemens/products/0004401572) (HB678GBS6B/58). See [Tested Appliances](https://github.com/thoukydides/homebridge-homeconnect/wiki/Testing).

## HomeKit Apps

Apple's Home app does not support all of the features of this plugin. Use one of the alternative [Recommended HomeKit Apps](https://github.com/thoukydides/homebridge-homeconnect/wiki/HomeKit-Apps) instead.

## Changelog

All notable changes to this project will be documented in [CHANGELOG.md](CHANGELOG.md).

## Reporting Issues

Report any issues on [GitHub](https://github.com/thoukydides/homebridge-homeconnect/issues/new/choose).

Please attach the relevant section of the Homebridge log file, either pasted into the issue or attached as a text file (*but not as a screenshot*). Extra debug should be enabled and captured if appropriate:
* **Homebridge debug logging:** Start Homebridge with the `-D` option to capture the *debug* level messages. These are used by this plugin to log basic information about each request to the Home Connect servers (but not the actual contents of the requests or responses) and other internal state. Please enable this for any issues that involve problems connecting to the Home Connect servers, API errors, or other problems with appliance state or control.
* **HomeKit Accessory Protocol (HAP) logging:** Setting the `DEBUG=*` environment variable before starting Homebridge results in verbose logging of all [HAP-NodeJS](https://github.com/KhaosT/HAP-NodeJS) HomeKit exchanges. Please enable this for any issues that involve problems controlling appliances from HomeKit or Siri.

Before raising an issue please check whether it relates to an expected [Error Message](https://github.com/thoukydides/homebridge-homeconnect/wiki/Errors) and whether any similar [issues already exist](https://github.com/thoukydides/homebridge-homeconnect/issues?utf8=%E2%9C%93&q=).

## License

> ISC License (ISC)<br>Copyright © 2019-2020 Alexander Thoukydides
>
> Permission to use, copy, modify, and/or distribute this software for any purpose with or without fee is hereby granted, provided that the above copyright notice and this permission notice appear in all copies.
>
> THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
