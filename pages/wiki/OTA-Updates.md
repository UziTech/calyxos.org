Decided to go with https://github.com/AndroidHardening/platform_packages_apps_Updater which is basically the previous implementation (CopperheadOS Updater) re-licensed to MIT.

# No longer current

## Previous Implemenation

### CopperheadOS Updater
Client: https://github.com/AndroidHardeningArchive/platform_packages_apps_Updater

Server: Any HTTP server + text file generated by https://github.com/AndroidHardeningArchive/script/blob/oreo-m2-s3-release/generate_metadata.py

Supports: Legacy + A/B

Pros:
* Simple implementation
* Basically non-existent server side, just need a file.

Cons:
* Licensing :(

# Alternatives

### LineageOS Updater
Client: https://github.com/LineageOS/android_packages_apps_Updater

Server: https://github.com/lineageos-infra/updater (and mirrorbits + https://github.com/lineageos-infra/mirrorbits-api optionally)

Supports: Legacy + A/B

Pros:
* Full fledged, feature rich updater

Cons:
* Complex implementation, even on the server side
* Would need to tweak the U/I to not show multiple updates

### Google's Sample Updater
Client: https://android.googlesource.com/platform/bootable/recovery/+/master/updater_sample/

Server: Any HTTP server + json file generated by https://android.googlesource.com/platform/bootable/recovery/+/master/updater_sample/tools/gen_update_config.py

Supports: A/B only

Pros:
* Google provided implementation with multiple tests
* Basically non-existent server side, just need a file.

Cons:
* No legacy support, can be added but will take some effort + testing. It's not that hard to install a legacy update, since that's handled by recovery and all we need to do is point it to the file and reboot.
* Need to implement code to check for updates periodically and download/install it as desired (automatic / on certain networks / etc).
* Need to add support for multiple channels (stable/beta/etc) - but the json config file means it would be simple, a few lines of extra code.
* Need to make some U/I tweaks to disable extra options, easy enough.