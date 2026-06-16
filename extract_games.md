# How to extract games names

With Heroic Games Launcher installed via Flatpak and with the below stores connected:

- EPIC games:
```
jq -r '.library | map(select(.install.is_dlc != true)) | .[].title' ~/.var/app/com.heroicgameslauncher.hgl/config/heroic/store_cache/legendary_library.json
```
- GOG games:
```
jq -r '.games | .[].title' ~/.var/app/com.heroicgameslauncher.hgl/config/heroic/store_cache/gog_library.json
```
- Amazon games:
```
jq -r '.library | map(select(.install.is_dlc != true)) | .[].title' ~/.var/app/com.heroicgameslauncher.hgl/config/heroic/store_cache/nile_library.json
```
