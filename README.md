# MpdMacOS

A Mpd (Music Player Daemon) client for macOS menubar with elegant UI and comprehensive playback control.

Created for Music Player Daemon eco-system with love.

## Core Features

### Menubar Integration
- **Live Song Display** - Shows currently playing song with scrolling text for long titles
- **Click to Control** - Click menubar text to open control menu
- **Visual Status Indicators** - Music note (♪) for playing, stop sign (■) for oneshot mode
- **Multiple Server Profiles** - Connect to different MPD servers with saved configurations

### MPD Control
- **Media Key Support** - Full integration with macOS media keys, Control Center, Touch Bar, and Siri
- **Global Hotkeys** - Ctrl+Option+F (Search), Ctrl+Option+L (Search), Ctrl+Option+R (Refresh)
- **Playback Control** - Play, pause, next, previous, seek, volume control
- **Stop After Current Song** - Toggle oneshot mode to stop after current track

### Search & Navigation
- **Search** - Search within current playlist with instant results and fuzzy matching
- **Go to Song** - Jump to current song with context (40 songs before/after)
- **Song Context Menus** - Add to queue, load playlists, set priorities

### Playlist Management
- **Playlist Loading** - Load any MPD playlist with visual indicators for current playlist
- **Queue Management** - Add songs to queue with priority support and visual queue indicators
- **Music Directory Browse** - Navigate full music library when no playlist loaded

### Rich Media Information
- **Detailed Tooltips** - Hover for song info, comment, genre, progress, format, volume
- **Progress Tracking** - Visual seek slider with click-to-seek functionality
- **Audio Format Display** - Shows bitrate, bit depth, channels (e.g., "192kHz/24-bit/2ch")
- **Volume Control** - Integrated volume slider in tooltip

## Requirements
- macOS 10.15 (Catalina) or later
- MPD server (local or remote)
- Accessibility permissions (optional, for global hotkeys)
