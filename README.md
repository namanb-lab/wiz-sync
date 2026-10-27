# WiZ Screen Sync

Ambient lighting for your **Philips WiZ** bulbs, with no extra hardware. This Android and Android TV app watches what is on your screen (YouTube, movies, games) and sends the dominant color and brightness to your WiZ bulbs over your local Wi-Fi, about 10 times a second.

> Unofficial project. Not affiliated with or endorsed by Philips, Signify or WiZ.
>
> Tested on TCL C6K Mini Led TV and it's work Fine with Youtube Video set to 1080P as some higher quality TV video starts lagging.
> 
> Tested on Android 17 Android Phone and here select any quality as it's not lagging, Depends on Device 

## Features

- **Screen color sync** for Android TV, Google TV, phones and tablets
- **Finds your bulbs automatically** and shows how many it found, with each bulb's IP, MAC, model, firmware, power state and Wi-Fi signal
- **Per-bulb switch** to include or leave out any bulb, remembered between launches and applied live
- **Blink button** to flash a bulb so you know which one is which
- **Color-accurate on WiZ bulbs**: ignores black bars and shadows, favors bright and colorful areas, sends pure hues so scenes don't turn pink, and falls back to white light for gray scenes (Still need some work)
- Runs entirely on your local network. No account, no cloud, no ads

## Download

Get the latest APK from the **[Releases page](../../releases/latest)**. Every push to this repo rebuilds it automatically.


# Setup on the bulbs

In the WiZ app, make sure **local communication** is allowed for your bulbs, and keep the TV or phone on the same Wi-Fi as the bulbs.

Open Wiz V2(Official App) - Setting(On top right corner) - Security - Allow Local - Allow All Control 

## How to Use
It also works on a phone: install the APK, tap **Start Sync** give Recording Permission, and play a video on the same device.


## Tuning

The look can be adjusted at the top of `SyncService.kt` (inside the workflow file):

| Setting | What it does | Default |
| --- | --- | --- |
| `minDim` | Lowest bulb brightness in percent | 40 |
| `gamma` | Lower means brighter in dark scenes | 0.6 |
| `satBoost` | Higher means more vivid colors | 2.2 |
| `minSat` | Colored scenes never get paler than this | 0.7 |
| `gainR`, `gainG`, `gainB` | Per-channel trim; lower `gainB` if colors look pink | 1.0, 1.0, 0.8 |

## Known limits

- Some TVs have no screen-capture permission dialog, and some return black frames for video. Those devices cannot be used.
- Wi-Fi bulbs update a few times per second, so this is mood lighting, not frame-accurate sync.
- All active bulbs get the same color.
- The APK is signed with a debug key that changes with each build, so uninstall the old version before installing a new one.
- Color Accuracy is not that great 
- Not work on DRM Protected App like Netflix 
