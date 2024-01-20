# KickrBikeInterceptor-Releases

A windows app that will attach to BLE Bike Trainers and expose them as DIRCON (Wahoo Direct Connect).
Idealy it is best to use a Wahoo Kickr Bike, but any trainer that supports the Bluetooth prococols: FTMS and Power Metter will work.

If the trainer is a Kickr Bike, app will do two things.

1) Allow you to open secondary "Always on top" window to see Kickr Bike Gears as they change.
2) KickrBikeInterceptor will inject gear data to [sauce4zwift](https://www.sauce.llc/products/sauce4zwift/) via Http posts.

The json format of the injected data is
```
["self", { "gears" : {"chainring": "<frontgear>", "cassette": "<reargear>" }}]
```

You can install my [sauce4zwift](https://www.sauce.llc/products/sauce4zwift/) Mod from [KickrBikeGearsS4ZMod](https://github.com/pwfulghum/KickrBikeGearsS4ZMod) for a clean integraion with [sauce4zwift](https://www.sauce.llc/products/sauce4zwift/) 

## Usage
You really have several options…

KickrBikeInterceptor has an “Open Gears Window” button where it will open a "always on top" window that you can place on top of zwift and you don’t need Sauce4Zwift. Or you can use the more elegant solution of sauce for zwift with [KickrBikeGearsS4ZMod](https://github.com/pwfulghum/KickrBikeGearsS4ZMod). I highly recommend sauce for zwift.

If you have kickr bike **WITHOUT** dircon, You **MUST** use KickrBikeInterceptor and have zwift connect to the “INTR KICKR bike” on the device connection screens. In this scenario, zwift is talking dircon to interceptor and interceptor is talking bluetooth to the bike. **You must start interceptor before zwift starts.**

If you have a kickr bike **WITH** dircon, you still need to run KickrBikeInterceptor, but zwift can connect to either bike dircon, or to interceptor dircon.

If you decide not to use the Sauce4Zwift integration, I would change the appsettings.json file (towards the bottom).

“Sauce”: { “url”: “” } (it will make sense when you see it.)

P.S . v1.0.0 of my mod had a typo that has been fixed in **v1.0.1** of the [KickrBikeGearsS4ZMod](https://github.com/pwfulghum/KickrBikeGearsS4ZMod)

## Notes - PLEASE READ
- The appsettings.json file must live in the same directory as the executable.
- The appsettings.json setting (TrainerName:mustMatch) specifies what BLE devices to consider to attach to.  Default is "BIKE", but if you want to attach to a normal KICKR, change to "KICKR".  If you have multiple bikes/trainers within bluetooth range, you can specifiy the exact name to match, or any part of the trainers name to match.  For example, string "BC4E" will match "KICKR BIKE BC4E".
- the appsettings.json setting (Sauce:url) specifies where the [sauce4zwift](https://www.sauce.llc/products/sauce4zwift/) webserver is running.  If you don't want Sauce integration you can just make this an empty string "".
- the appsetings.json setting (NLog:rules:minLevel) specifies level of verbosity in the log file.  (NLog:rules:minLevel).   If log is too verbose try, "Info" instead.
- Log files are created in /users/<you>/appdata/local/KickrBikeInterceptor/logs directory.  1 log per execution, maximum 9 log files.

Need help?  Post an issue.
