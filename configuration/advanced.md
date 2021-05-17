---
title: Other Settings (Advanced)
nav_order: 6
layout: default
parent: Configuration
---
### Pokemon aliasing

The `pokemonAlias.json` file provides a mechanism for aliasing commonly mis-spelt pokemon.
It currently has an English focus, but you can update your local copy.  Contributions for
good additions will certainly be considered for more widespread distribution so please
share

### Shortened URLs

Wrap in `<S<` and `>S>` for Poracle to pass the URL through a shortener
(currently only *xxxxx* is supported)

### Changing discord emoticons

### PVP Scanner

### Facebook

### Delegated Administration

You can configure that certain users are able to make changes to the tracking in channels, groups, or on webhooks.

For discord this looks like this:  The ID number in channel tracking can be a guild (can change tracking for all channels in a guild), a category (all channels in a category), or an individual category.
The admin

```json
     "delegatedAdministration": {
             "channelTracking": {
                "794678214236438569": [ "745735260020539513" ]
            },
            "webhookTracking": {
                "poracle-test": ["726564415431770202" ]
            }
        },
```
For telegram, the channelTracking can be the name of a channel or the id number of a group.

### Reconciliation

The reconciliation that runs every <n> hours can now do even more!
If the telegram option registerOnStart is set then this is run on a /start message (which is sent automatically by the telegram client). This means that users who are in the appropriate feeder channels will be registered on a /start and don't need to do a /poracle.

```json
"reconciliation": {
    "discord": {
        "updateUserNames": false,                // Follow discord username changes
        "removeInvalidUsers": true,              // Whether users who lose roles should be de-registered
        "registerNewUsers": false,               // Whether users who are granted roles are auto-registered
        "updateChannelNames": true,              // Whether channel names are kept in sync
        "updateChannelNotes": false,             // Whether channel notes are updated to contain guild name / category
        "unregisterMissingChannels": false       // Whether channels that are deleted from discord are removed from database
    },
    "telegram": {
        "updateUserNames": false,                // Follow telegram username changes
        "removeInvalidUsers": true               // Whether users are automatically removed
    }
},
```
