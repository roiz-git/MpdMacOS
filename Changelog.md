## [10.0.7] - 2025-10-02

- Fix search result click off-by-one error - clicking on search results now plays the correct song
- Fix Go to Song highlighting off-by-one error - "Go to Song" now highlights the correct currently playing song

## [10.0.6] - 2025-10-01
- Fixed "Go to Song" highlighting bug - Now correctly highlights the currently playing song
- Disabled debug logging for releases - Installed apps no longer create ~/debug.log files
- Added Comment tag support - Comment metadata now appears in song tooltips
- Fixed hotkey mapping - Ctrl+Option+L properly triggers "Go to Current Song"

## [10.0.5] - 2025-09-28

### Improved
- macOS Sleep Compliance - App now properly sleeps when your Mac goes to sleep, preventing connection flooding and battery drain

## [10.0.4] - 2025-09-28

## Improved
- Update mechanism

## [10.0.3] - 2025-09-28

### Added
- Automatic update checking and installation
- "Check for Updates..." menu item for manual update checks

### Changed
- Moved "Stop After Current" menu item above "Search" for improved menu organization
- Reorganized menu items for better accessibility

## [10.0.1] - 2025-09-28

### Added
- Global keyboard shortcuts for system-wide music control:
  - Cmd+Ctrl+Option+Up: Play/Pause
  - Cmd+Ctrl+Option+Down: Stop
  - Cmd+Ctrl+Option+Left/Right: Previous/Next track
  - Cmd+Ctrl+Option +/-: Volume control
  - Ctrl+Option+F: Open search
  - Ctrl+Option+R: Refresh connection

### Improved
- Enhanced global shortcut responsiveness and reliability

## [9.6.8] - 2025-09-27 (Initial Release)

### Added
- MPD client functionality integrated into macOS menu bar
- Real-time song information display with scrolling text support
- Music playback controls (play, pause, stop, next, previous)
- Multiple MPD server profile management
- Queue management with priority support
- Playlist loading and management
- Music library search functionality
- "Go to Current Song" navigation feature
- Hover tooltip with detailed song information and playback progress
- Volume control integration
- Media key support for keyboard control
- Launch at startup option
- Automatic MPD server connection management
- Native macOS design with dark/light mode support
