# Custom Jellyfin CSS Theme

A custom CSS theme for Jellyfin that builds upon ElegantFin and adds library organization plus DVR/Live TV hiding functionality.

## Features

- **Base Theme**: Built on top of the beautiful ElegantFin theme
- **Library Organization**: Automatically orders your home page libraries (Movies → Shows → Music → Collections → Playlists)
- **Media bar (slideshow) fixes**: Alignment, stage-height, and dots/arrows patches for the [Jellyfin Media Bar plugin](https://github.com/IAmParadox27/jellyfin-plugin-media-bar) v6 under ElegantFin

## Installation

To use this theme in your Jellyfin server:

1. Open your Jellyfin admin dashboard
2. Go to **Dashboard** → **Branding** → **Custom CSS**
3. Add the following import statement:

```css
@import url("https://cdn.jsdelivr.net/gh/TiddlyQwert/straylcb-jellyfin-css@main/Theme/jellyfin-theme.css");
```

## Media bar plugin (pinned)

The media bar plugin's CSS/JS are injected into `index.html` by the plugin itself, **not** by this theme. Its source ref is controlled by the plugin's own config, which survives Jellyfin upgrades (unlike editing `index.html`).

**Dashboard → Plugins → Media Bar → Settings:**
- **Version**: `500c01292cdebf8c18ae6984ede10627cf106365` (a commit SHA, not `main`)
- **Allow unpinned refs**: unchecked

This pins the frontend to a known-good commit so upstream `@main` updates can't silently break the layout again — this is what bit us on 2026-10-06. The config is stored server-side in `plugins/configurations/Jellyfin.Plugin.MediaBar.xml` (`VersionString` + `AllowUnpinnedRefs`). To update to a newer plugin frontend later, replace the SHA with the latest commit on the plugin repo's `main` branch.

## ElegantFin pins

The ElegantFin imports at the top of `Theme/jellyfin-theme.css` are pinned to commit SHAs for the same reason (nightly `@main` builds once broke the media bar layout). To update ElegantFin:

1. Check the latest commits: `https://github.com/lscambo13/ElegantFin/commits/main`
2. Replace the SHA in the matching `@import` line (main theme and/or media-bar add-on)
3. Purge the CDN: `https://purge.jsdelivr.net/gh/TiddlyQwert/straylcb-jellyfin-css@main/Theme/jellyfin-theme.css`
4. After pushing, allow a few minutes for jsDelivr's branch cache to refresh before expecting changes to appear (purge immediately after a push can re-cache stale content)

## Customization

If you need to modify the library order or show/hide different elements, you can:

1. Fork this repository
2. Edit `Theme/jellyfin-theme.css`
3. Update the library data-id values to match your specific Jellyfin setup
4. Commit your changes

**Finding Your Library IDs**: The current data-id values are specific to the original setup. To find your own library IDs, inspect your Jellyfin home page HTML and look for `data-id` attributes on library cards.

## Development

The main theme file is located at `Theme/jellyfin-theme.css`. Make your changes there and commit to the main branch. The CDN will automatically update within a few minutes (see the note about jsDelivr cache delays above).

## Structure

```
├── Theme/
│   └── jellyfin-theme.css     # Main theme file with ElegantFin base + customizations
└── README.md                  # This file
```

## Credits

- Base theme: [ElegantFin](https://github.com/lscambo13/ElegantFin) by lscambo13
- Media bar plugin: [jellyfin-plugin-media-bar](https://github.com/IAmParadox27/jellyfin-plugin-media-bar) by IAmParadox27
- Customizations: Library organization, DVR/Live TV hiding, media bar v6 alignment fixes
