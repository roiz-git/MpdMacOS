# ~~MpdMacOS~~ Maestro - MPD Client

MPD client for macOS menubar with elegant UI and comprehensive playback control. Created for Music Player Daemon ecosystem with love.

## Core Features

### Menubar Integration
- **Live Song Display** - Shows currently playing song with scrolling text for long titles
- **Click to Control** - Click menubar text to open control menu
- **Visual Status Indicators** - Music note (♪) for playing, stop sign (■) for Stop After Current mode
- **Next Song Preview** - Shows upcoming song with clickable "Go to Song" functionality
- **Multiple Server Profiles** - Connect to different MPD servers with saved configurations

### MPD Control
- **Media Key Support** - Full integration with macOS media keys, Control Center, Touch Bar, and Siri
- **Global Keyboard Shortcuts** - System-wide hotkeys without requiring accessibility permissions:
  - Cmd+Ctrl+Option+Up: Play/Pause
  - Cmd+Ctrl+Option+Down: Stop
  - Cmd+Ctrl+Option+Left/Right: Previous/Next track
  - Cmd+Ctrl+Option +/-: Volume control
  - Ctrl+Option+F: Open search
  - Ctrl+Option+R: Refresh connection
- **Playback Control** - Play, pause, next, previous, seek, volume control
- **Stop After Current Song** - Toggle mode to stop after current track finishes

### Search & Navigation
- **Search** - Search within current playlist with instant results and fuzzy matching
- **Search Music Dir** - Search your entire music library while browsing a playlist
- **Go to Song** - Jump to current song with context (40 songs before/after)
- **Next Song Navigation** - Click next song preview to jump to its position in playlist
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

### Updates & Integration
- **Automatic Updates** - Secure automatic app updates with Sparkle framework
- **Script Integration** - Export MPD connection info for external scripts and automation
- **Launch at Startup** - Optional automatic launch on system startup

## Requirements
- macOS 10.13 (High Sierra) or later
- MPD server (local or remote)
- Optional: Accessibility permissions for enhanced media key control

## Usage

The app automatically connects to your MPD server and displays the currently playing song in the menubar. The display updates automatically when the song changes.

### Getting Started
1. Launch Maestro
2. Click the menubar text to open the control menu
3. Add/Edit MPD server profiles in Settings
4. Use global shortcuts or media keys to control playback

### Context Menu
- **Server Information** - Shows connected MPD server and next song preview
- **Playback Controls** - Play, pause, stop, next, previous
- **Search** - Search current playlist or entire music library
- **Go to Song** - Jump to current song with surrounding context
- **Queue Management** - View and manage queued songs with priorities
- **Playlists** - Load any saved MPD playlist
- **Stop After Current** - Toggle oneshot mode
- **Settings** - Manage server profiles and app preferences

### Search Features
- **Local Search** - Search within current playlist with instant results
- **Search Music Dir** - Expands search to your entire music library
- **Context Menus** - Right-click any result to add to queue or load playlist

### Global Shortcuts
Control MPD from any application:
- **Cmd+Ctrl+Option+Up** - Play/Pause
- **Cmd+Ctrl+Option+Down** - Stop
- **Cmd+Ctrl+Option+Left** - Previous track
- **Cmd+Ctrl+Option+Right** - Next track
- **Cmd+Ctrl+Option++** - Volume up
- **Cmd+Ctrl+Option+-** - Volume down
- **Ctrl+Option+F** - Open search
- **Ctrl+Option+R** - Refresh connection

### Visual Indicators
- **Playing:** Song title with artist and album info, music note (♪) prefix
- **Stopped:** Hostname or "Queue Empty" with music note (♪)
- **Stop After Current:** Stop sign (■) prefix in menubar and menu
- **Next Song:** Shows upcoming track below server name
- **Current Playlist:** Checkmark (✓) next to active playlist
- **Queue Items:** Shows count and priority levels
