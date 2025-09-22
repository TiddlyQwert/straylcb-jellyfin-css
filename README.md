# Custom Jellyfin CSS Theme

A custom CSS theme for Jellyfin that builds upon ElegantFin and adds library organization plus DVR/Live TV hiding functionality.

## Features

- **Base Theme**: Built on top of the beautiful ElegantFin theme
- **Library Organization**: Automatically orders your home page libraries (Movies → Shows → Music → Collections → Playlists)
- **DVR/Recording Cleanup**: Completely hides all DVR, recording, and Live TV elements
- **Clean Interface**: Removes clutter for users who don't use Jellyfin's TV recording features

## What Gets Hidden

- DVR-related libraries (Recorded Movies, Recorded Shows, Recordings)
- Live TV library from home page
- "On Now" section
- All "Record" buttons throughout the interface
- "Recordings" tab in navigation
- Recording-related menu items and links

## Installation

To use this theme in your Jellyfin server:

1. Open your Jellyfin admin dashboard
2. Go to **Dashboard** → **General** → **Custom CSS**
3. Add the following import statement:

```css
@import url("https://cdn.jsdelivr.net/gh/TiddlyQwert/straylcb-jellyfin-css@latest/Theme/jellyfin-theme.css");
```

## Customization

If you need to modify the library order or show/hide different elements, you can:

1. Fork this repository
2. Edit `Theme/jellyfin-theme.css`
3. Update the library data-id values to match your specific Jellyfin setup
4. Commit your changes

**Finding Your Library IDs**: The current data-id values are specific to the original setup. To find your own library IDs, inspect your Jellyfin home page HTML and look for `data-id` attributes on library cards.

## Development

The main theme file is located at `Theme/jellyfin-theme.css`. Make your changes there and commit to the main branch. The CDN will automatically update within a few minutes.

## Structure

```
├── Theme/
│   └── jellyfin-theme.css     # Main theme file with ElegantFin base + customizations
└── README.md                  # This file
```

## Credits

- Base theme: [ElegantFin](https://github.com/lscambo13/ElegantFin) by lscambo13
- Customizations: Library organization and DVR/Live TV hiding
