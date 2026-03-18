# Slack Desktop Launcher Bookmark

A single HTML file that opens the Slack desktop app when loaded in a browser. Designed to live in your bookmarks bar as a quick-launch shortcut.

## How It Works

The page fires `slack://open` via JavaScript on load. macOS (and Windows) recognize Slack's custom protocol handler and launch the app. A manual fallback link is included if the auto-redirect doesn't trigger.

The file uses Slack's hosted favicon so the bookmark displays the Slack icon in your browser's bookmarks bar.

## Setup

1. Save `index.html` somewhere stable on your machine (e.g., `~/Documents/bookmarks/`)
2. Open the file in your browser once to confirm it works
3. Drag it to your bookmarks bar, or bookmark the `file:///` URL manually

## Limitations

- **First-run confirmation:** Browsers show a "This site wants to open Slack.app" dialog the first time. Check "Always allow" to suppress it going forward.
- **No install detection:** If Slack isn't installed, the protocol silently fails or the browser shows a generic error. There's no reliable cross-browser way to detect whether the app exists.
- **Favicon caching:** The icon pulls from Slack's CDN (`a.slack-edge.com`). If you're offline, the favicon won't load, but the launcher still works.

## Customization

To open a specific workspace or channel instead of just launching Slack, change the URL in both the `<script>` tag and the fallback `<a>` tag:

| Target | URL |
|---|---|
| Default (just open Slack) | `slack://open` |
| Specific workspace | `slack://open?team=T12345` |
| Specific channel | `slack://channel?team=T12345&id=C12345` |

Find your team and channel IDs by right-clicking a channel in Slack and choosing "Copy link."

## License

Do whatever you want with this. It's a single HTML file.