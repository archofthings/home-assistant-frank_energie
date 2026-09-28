# Frank Energie for Home Assistant: this repository has moved

> [!IMPORTANT]
> Development continues at **[archofthings/home-assistant-frank-energie](https://github.com/archofthings/home-assistant-frank-energie)**.
> This fork is no longer updated. Please install from, and report issues at, the new repository.

[![Open your Home Assistant instance and open the new repository in HACS.](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=archofthings&repository=home-assistant-frank-energie&category=integration)

## What's new in the new repository

The original integration ([bajansen/home-assistant-frank_energie](https://github.com/bajansen/home-assistant-frank_energie)) stopped working in 2026, when Frank Energie changed its API. The new repository fixes that and adds more:

- **Works with the new Frank Energie API** (`python-frank-energie` 2026.9.20).
- **15-minute prices**: sensors switch to the current quarter-hour price at :00, :15, :30 and :45. Daylight-saving days (92 or 100 slots) and the switch at midnight are handled.
- **More reliable updates**: missing prices for tomorrow, network errors and API errors no longer break the integration. The last known prices stay available while they still cover the future.
- **Better login handling**:
  - Tokens are renewed and saved automatically, so a restart doesn't force a new login.
  - After a successful token renewal the update is retried immediately, instead of waiting up to an hour for fresh data.
  - Logging in again keeps your settings.
  - Logging in again with a different account is refused with a clear message, instead of mixing up the two accounts' data. Add the other account as a separate integration instead.
  - Connection problems during login show a clear error.
- **Your delivery address is detected automatically** when you log in.
- **Accounts without gas and Belgian accounts** are supported: public fallback prices follow your account's country.
- **Clearer sensor states**: sensors show *unavailable* instead of an outdated price when there's no data. Cost sensors no longer disappear when there's no month summary yet.
- **Smaller recorder footprint**: the long `prices` attribute is no longer stored in the history database.
- **Working HACS releases**: the release workflow now attaches `frank_energie.zip`, which fixes the 404 download error.
- **A rewritten test suite** that runs in CI on Python 3.14 with Home Assistant 2026.9.

See the [new README](https://github.com/archofthings/home-assistant-frank-energie#readme) for the full documentation.

## Switching to the new repository

Your configured integration, entities and history are kept; the integration domain and entity IDs don't change.

1. In HACS, open **Frank Energie** and choose **Remove**. This removes only the integration's files.
2. Remove `https://github.com/archofthings/home-assistant-frank_energie` from **Custom repositories**.
3. Add `https://github.com/archofthings/home-assistant-frank-energie` as a custom repository of type **Integration**, then download **Frank Energie**.
4. Restart Home Assistant.

Requires Home Assistant 2026.9 or newer.

---

*Nederlands:* deze repository is verhuisd naar [archofthings/home-assistant-frank-energie](https://github.com/archofthings/home-assistant-frank-energie). Installeer de integratie en meld problemen daar.
