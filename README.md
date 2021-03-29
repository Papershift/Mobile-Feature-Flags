# Mobile Feature Flags

General structure of the JSON files:
1. Android & iOS have separate folders so they can be turned on/off independently.
1. Each app has it's own file so there's only relevant flags per app.
1. For features that can only be turned on or off, the key is the name of the feature & the value is an array of SemVer version ranges in which the feature should be turned on. For example:

   ```json
   [
     { "from": "4.2.2", "to": "999.999.999" },
     { "from": "4.2.0", "to": "4.2.0" },
   ]
   ```

   This means: Allow the feature for all versions greater or equal to `4.2.2`. Also, allow the feature for version `4.2.0`. This can be used when the feature was shipped in version `4.2.0` and there was a bug with it in `4.2.1`, so it's turned off there.


To fetch the feature flag settings, use this URL structure (replace `<platform>` & `<app>` accordingly):
```
https://raw.githubusercontent.com/Papershift/Mobile-Feature-Flags/main/<platform>/<app>.json
```

For example, the full URL for Station-Android would be:
```
https://raw.githubusercontent.com/Papershift/Mobile-Feature-Flags/main/Android/Station.json
```


## Station

- `retry_block_on_fail`: Turns on/off [this feature](https://app.asana.com/0/1198086487644161/1199974969009138/f).
