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

## Notes
- Log files are created in /users/<you>/appdata/local/KickrBikeInterceptor/logs directory.  1 log per execution, maximum 9 log files.
- The appsettings.json file must live in the same directory as the executable.
- The appsettings.json file (TrainerName:mustMatch) specifies what BLE devices to consider to attach to.  Default is "BIKE", but if you want to attach to a normal KICKR, change to "KICKR".  If you have multiple bikes/trainers within bluetooth range, you can specifiy the exact name to match.
- the appsettings.json setting (Sauce:url) specifies where the [sauce4zwift](https://www.sauce.llc/products/sauce4zwift/) webserver is running.  If you don't want Sauce integration you can just make this an empty string "".
- the appsetings.json file specifies level of verbosity in the log file.  (NLog:rules:minLevel).   Too verbose try, "Info" instead
