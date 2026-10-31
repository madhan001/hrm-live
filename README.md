# HRM Live

Real-time heart rate monitor for any Bluetooth LE chest strap or armband, running entirely in your browser. No account, no server, no tracking. Nothing is uploaded.

## Features

- Live BPM with heart-rate zones (percent of max HR, configurable)
- Real-time chart with zone bands, hover readout, and 1 min to whole-session windows
- RR intervals and RMSSD (a heart rate variability measure), skin contact, battery, energy expended, sensor location
- Time in each zone
- Current BPM shown in the browser tab icon and title
- CSV export
- Installable as an app (PWA), works offline once loaded
- Auto-reconnect if the strap drops, and screen wake lock while connected
- Demo mode for trying the UI without a monitor

## Compatibility

Works with any monitor that implements the standard Bluetooth **Heart Rate Service** (0x180D). That covers most straps and armbands (Polar, Wahoo, Garmin HRM, Coospo, Magene, Helio and others), plus some watches that can broadcast heart rate.

| Platform | Browser | Works |
|---|---|---|
| Windows, macOS, Linux, ChromeOS | Chrome, Edge, Opera | Yes |
| Android | Chrome, Edge, Opera | Yes |
| Brave | any | Needs `brave://flags/#brave-web-bluetooth-api` enabled; on Linux also `#enable-web-bluetooth` |
| iPhone / iPad | Bluefy browser | Yes. Safari does not support Web Bluetooth |
| Firefox, Safari | any | No |

Tips:
- Put the monitor on, or wet the contacts, so it starts advertising.
- Most straps allow only one connection at a time. Disconnect other apps first.
- If your device doesn't show up, turn on **Settings → Show all Bluetooth devices**.

## Run locally

It's a static site with no build step:

```
python3 -m http.server 8000
```

then open <http://localhost:8000>. Web Bluetooth requires HTTPS or `localhost`.

## Privacy

All processing happens in the page. Settings (max HR etc.) are kept in your browser's `localStorage`. Session data is held in memory only and is lost on reload unless you export the CSV.

## License

[MIT](LICENSE)
