# iBeacon Cordova Plugin - Frequently Asked Questions

### How do I debug notifications in the background?

Enable the debug logging and inspect the console logs of your device through XCode.

### I would like to customise the permission dialogs on iOS. How do I do that?

Introduce an iOS specific preference in your config.xml, something like this:

```xml
<preference name="NSLocationWhenInUseUsageDescription" value="This app would like to scan for iBeacons while it is in use." />

<preference name="NSLocationAlwaysUsageDescription" value="This app would like to scan for iBeacons even when in the background." />
```

### I would like to customise the AltBeacon library scans period. How do I do that?

Introduce an Android specific preference in your config.xml, something like this:

```xml
<preference name="BeaconForegroundScanPeriod" value="5000" />
```

The default is 200 for the mentioned configuration value.

### I would like to customise how frequently the AltBeacon library scans for proximity devices (beacons). How do I do that?

Introduce an Android specific preference in your config.xml, something like this:

```xml
<preference name="BeaconForegroundBetweenScanPeriod" value="5000" />
```

This will ensure that the AltBeacon library will wait five seconds in-between foreground scans.
The default is 0 for the mentioned configuration value.

### 'NSInternalInconsistencyException' Exception at Application Startup: ```Assertion failure in -[CLLocationManager setAllowsBackgroundLocationUpdates:]```

This most likely happens because you forgot to enable the ```Background Modes``` capability by switching
it to ```ON``` and then ticking ```Location updates``` as well. The messages and the stack trace may lead
you to think that this is something to do with the UIWebView/WKWebView that you are using, but it is not.
