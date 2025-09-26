# MpdmacOS

A Mpd Client for macOS that displays the currently playing MPD song in the menubar, allows playlist and queue management and integrates with the Mac's media keys.

## Version History

### v9.6.2
- **Accessibility Permission Setup Dialog** - Added elegant first-launch dialog to explain and request accessibility permissions for global hotkey features
- **Eliminated Permission Prompts** - Replaced repeated accessibility permission prompts with one-time setup dialog that appears only on first launch
- **Professional Setup Experience** - Setup dialog includes app icon and clear explanation of global hotkey features with option to enable or skip
- **Silent Permission Handling** - After initial setup, accessibility permission checks work silently without interrupting user workflow
- All features from v9.6.1

### v9.6.1
- **Enhanced Go to Song Window Interaction** - Fixed inconsistent menubar click behavior where clicking on menubar text sometimes failed to close the Go to Song window
- **Reliable Window Event Handling** - Implemented robust window-level mouse event detection with smart hit testing to differentiate between menubar text and result list clicks
- **Improved User Experience** - Go to Song window now consistently closes when clicking on menubar scrolling text, matching ESC key functionality for seamless interaction
- All features from v9.6.0

### v9.6.0
- **Go to Song Feature** - Added "Go to Song" menu item that opens search window pre-populated with current song plus 40 songs before and after in queue
- **Current Song Highlighting** - Currently playing song appears with music note prefix "♪" for easy identification in Go to Song results
- **Context Menu Integration** - All songs in Go to Song list have full 3-dot context menus with queue and playlist options  
- **Enhanced Window Management** - Go to Song window extends to dock edge without hiding content, with proper Escape key handling
- **Scrolling Text Preservation** - Menubar text continues scrolling while Go to Song window is open for uninterrupted status display
- **Dynamic About Dialog** - About dialog now reads version information directly from app bundle for automatic version synchronization
- **Improved Logging System** - Fixed truncated log messages in debug output through enhanced file I/O handling
- All features from v9.5.0

### v9.5.0
- **Stop After Current Song Feature** - Added menu item to enable MPD's "single oneshot" mode, automatically stopping playback after the current song finishes
- **Visual Oneshot Indicators** - Stop sign (■) prefix appears in menubar and tooltip when oneshot mode is active for clear visual feedback
- **Menu Item Toggle Functionality** - "Stop After Current Song" menu item acts as a toggle - click to enable/disable with music note (♪) indicator when active
- **Immediate Visual Updates** - All indicators update instantly when toggling oneshot mode, providing immediate user feedback
- All features from v9.4.2

### v9.4.2
- **Eliminated Duplicate Status Updates** - Implemented debounced status updates with 200ms delay to coalesce rapid MPD events, reducing duplicate queries from 2+ to 1 per event group
- **Enhanced Event Processing** - Combined playlist and player event handling with intelligent debouncing to prevent redundant MPD status calls during media key operations
- **Optimized Queue Management** - Modified checkAndRemovePlayingFromQueue() to accept song data as parameter, eliminating independent MPD queries by reusing status update data
- **Function Renaming Cleanup** - Renamed updateMpdStatusNetcat() to updateMpdStatus() throughout codebase for accurate naming after libmpdclient migration
- **Improved Performance** - Status updates now efficiently handle rapid successive events (song changes, media key presses) with single MPD query instead of multiple redundant calls
- All features from v9.4.1

### v9.4.1
- **Queue Count Caching** - Added cachedQueueCount and queueCountCacheValid to prevent redundant calculations
- **Smart Cache Invalidation** - Queue count cache invalidates when priorities change or playlist cache refreshes
- **Optimized Queue Performance** - Reduced queue checking from 3 checks to 1 check per song change
- **Enhanced Cache Management** - Improved consistency across priority changes and playlist operations
- All features from v9.4.0

### v9.4.0
- **Enhanced Volume Slider UX** - Volume slider now only sends MPD commands when dragging stops, matching seek slider behavior for smoother interaction
- **Robust Custom Mouse Tracking** - Replaced standard NSSlider mouse handling with custom tracking pattern using window?.nextEvent() for reliable drag detection
- **Fixed Audio Format Display** - Resolved tooltip showing "unknown format" by implementing proper libmpdclient audio format extraction from mpd_status_get_audio_format()
- **Corrected Format Value Display** - Fixed audio format showing incorrect values (224 instead of f) by handling MPD special format values (0xe0 for float, 0xe1 for DSD)
- **Code Cleanup** - Removed unused executeCommand() function (~50 lines) that was never called after migration to libmpdclient
- **Reduced Log Noise** - Removed verbose volume drag logging for cleaner debug output
- All features from v9.3.2

### v9.3.5
- **Enhanced libmpdclient Connection Handling** - Improved connection stability and error handling for MPD communication
- **Performance Optimization** - Reduced connection overhead and improved response times for MPD operations
- All features from v9.3.4

### v9.3.4
- **Code Cleanup and Optimization** - Removed unused code and streamlined MPD communication pathways
- **Memory Management Improvements** - Enhanced memory handling for libmpdclient operations
- **Stability Improvements** - Fixed edge cases in MPD connection handling
- All features from v9.3.3

### v9.3.3
- **Media Control Migration** - Final migration to libmpdclient for media key operations and MPD server communication
- **Enhanced Performance** - Complete elimination of legacy mpc command dependencies for core functionality
- **Improved Reliability** - Native library integration provides more stable MPD server interactions
- All features from v9.3.2

### v9.3.2
- **Playlist Listing Migration** - Migrated playlist listing from `mpc lsplaylists` to libmpdclient `mpd_send_list_playlists` for improved performance
- **Removed Legacy Support** - Completely eliminated mpc-based playlist listing code, no legacy fallback needed
- **Enhanced Playlist Loading** - Playlist menus now load faster using native libmpdclient instead of shell process execution
- All features from v9.3.1

### v9.3.1
- **Playlist Operations Migration** - Migrated playlist loading and music directory operations from mpc to libmpdclient for improved performance
- **Fixed Playlist Indicators** - Playlist menu indicators now correctly show current playlist by reading `lastloadedplaylist` from MPD status
- **Enhanced Indicator Logic** - Music dir mode shows no indicators, only actual playlists display ♪ symbols for better UX
- **Code Cleanup** - Removed 200+ lines of deprecated search implementation code and unused mpc-based functions
- All features from v9.3.0

### v9.3.0
- **Complete Migration to libmpdclient** - Replaced all netcat-based MPD communication with native libmpdclient library for enhanced performance and reliability
- **Self-Contained Library Bundle** - libmpdclient now bundled within app, eliminating external Homebrew dependencies for MPD communication
- **Optimized MPD Protocol Handling** - Native C library integration provides faster, more efficient MPD server communication than shell commands
- **Enhanced Performance** - Eliminated process spawning overhead for MPD operations, resulting in smoother status updates and playlist operations  
- **Improved Connection Reliability** - Direct library connections replace brittle netcat timeout mechanisms
- **Cleaner Codebase** - Removed all deprecated netcat-based functions and legacy MPD parsing code
- All features from v9.2.0

### v9.2.0
- **Queue Menu Context Actions** - Added right-click context menu for queue items with "Play Now" and "Remove from Queue" options
- **Intelligent Queue Management** - Left-click on queue items now plays song immediately and removes it from queue for intuitive behavior
- **Real-time Queue Updates** - Queue menu automatically updates when queued songs start playing, removing completed items instantly
- **Optimized Queue Checking** - Queue status checks only run when songs are actually queued, improving performance
- **Enhanced Menu Responsiveness** - Immediate cache updates and menu refreshes ensure UI stays perfectly synchronized with MPD state
- All features from v9.1.1

### v9.1.1
- **Fixed 3-Dot Context Menu Positioning** - Context menu from search result 3-dot buttons now appears at correct height aligned with button
- **Improved Menu Coordinate Calculation** - Replaced synthetic event approach with direct menu positioning using button center coordinates
- **Enhanced Search Result Interaction** - Better user experience when accessing context menus from search results
- All features from v9.1.0

### v9.1.0
- **Dynamic Search Window Width** - Intelligent search window width calculation based on actual content length and screen dimensions
- **Screen-Aware Sizing** - Search window respects dock position and menu bar, using only visible screen area for calculations
- **Adaptive Content Accommodation** - Minimum 500px width with generous 120px padding to prevent title truncation
- **Optimized Display Boundaries** - Maximum width limited to 90% of available screen width for better desktop integration
- **Enhanced Debug Logging** - Comprehensive screen dimension and width calculation logging for troubleshooting
- All features from v9.0.0

### v9.0.0
- **Intelligent Playlist Detection** - Proper playlist state detection using MPD's `lastloadedplaylist` field
- **Enhanced Cache Efficiency** - Removed unnecessary cache refresh triggers for priority changes that don't affect playlist content
- **Unified MPD Communication** - Cache refresh now uses existing MPD_DIRECT status data instead of separate netcat calls
- **Improved Startup Performance** - Cache refresh leverages established connection patterns for faster initialization
- **Better Debug Visibility** - Added comprehensive netcat failure logging for troubleshooting connection issues
- **Accurate State Reporting** - Distinguishes between "Queue Empty", "Music dir mode", and named playlist states
- All features from v8.2.0

### v8.2.0
- **Queue Menu Implementation** - Added "Queue (X)" menu item above Playlists showing queued songs sorted by priority (Z-A)
- **Dynamic Queue Display** - Menu shows count of queued items, disabled when empty, with clickable submenu to play queued songs
- **Smart Cache Management** - Playlist cache only refreshes when queued items exist, preventing unnecessary overhead
- **Optimized Priority Detection** - Uses `mpc playlist --with-prio` for efficient queue item detection
- **Improved Startup Reliability** - Increased song info fetch timeout from 3 to 8 seconds with retry mechanism for better startup detection
- **Enhanced Launch Experience** - App now correctly displays current song instead of hostname when launched while music is playing
- All features from v8.1.1

### v8.1.1
- **Enhanced Cache Synchronization** - Playlist cache automatically refreshes when queueing songs from search results
- **Improved Menu Organization** - Moved Refresh menu item to better position above About for cleaner menu structure  
- **MPD Server as Single Source of Truth** - Ensures cache consistency with server state after queue operations
- All features from v8.1.0

### v8.1.0
- **Streamlined Search Interface** - Completely removed normal search functionality, leaving only optimized local search
- **Simplified User Experience** - Single "Search" option in context menu now exclusively uses instant cached data lookup
- **Reduced Code Complexity** - Removed ~300 lines of shell command generation and process management code
- **Enhanced Performance** - Eliminated network-based search operations in favor of instant local filtering
- **Cleaner Architecture** - Simplified search flow with consistent local-only search behavior
- All features from v8.0.1

### v8.0.1
- **Optimized Status Updates** - Added guard variable to prevent duplicate MPD command executions during rapid status changes
- **Improved Performance** - Eliminated concurrent status update calls that were causing redundant network traffic
- **Enhanced Debugging** - Better logging for status update flow control and duplicate prevention
- All features from v8.0.0

### v8.0.0
- **Search Local Implementation** - Complete local search functionality using cached playlist data for instant results
- **Intelligent Cache Refresh** - Playlist cache automatically detects changes using size comparison instead of unreliable MPD protocol
- **Thread-Safe Data Management** - Fixed race conditions in cached song data to prevent application crashes
- **Enhanced Search UI** - Fixed 3-dots context menu positioning to account for scrollbar space in all result scenarios
- **Optimized Cache Pipeline** - Resolved pipe deadlocks in cache refresh process for large playlists (11,000+ songs)
- **Isolated Search Architecture** - Complete separation between cache refresh and search operations with timeout protection
- **Robust Playlist Detection** - Reliable playlist change detection works across all MPD server configurations
- All features from v7.1.6

### v7.1.6
- **Playlist Cache System** - Implemented background playlist cache using JSON format for improved performance
- **Smart Cache Management** - Cache automatically refreshes on app startup, MPD connection changes, and playlist modification events
- **Dynamic About Dialog** - About dialog now reads version dynamically from app bundle instead of hardcoded value
- **Cache Independence** - New cache system operates independently without affecting existing search or menu functionality
- **MPD Protocol Integration** - Cache refresh triggered by MPD idle events for real-time playlist synchronization
- All features from v7.1.5

### v7.1.5
- **Music Note Icon Restored** - Added ♪ prefix to stopped state displays in menubar
- **Enhanced Stopped State Display** - Shows "♪ localhost" when server stopped with songs, "♪ Queue Empty" when no songs
- **Corrected Documentation** - Fixed README to match actual behavior with music note icon
- **Search Spinner Fix** - Fixed spinner overlays not disappearing when search completes or text field becomes empty
- **Improved Search UX** - Spinner overlays now properly hide in all scenarios (completion, error, empty field)
- All features from v7.1.4

### v7.1.4
- **Code Cleanup** - Removed broken playlist cache system that never functioned properly
- **Fixed Non-Existent Field Detection** - Eliminated cache code that tried to use non-existent 'playlist:' field from mpc status
- **Performance Improvement** - Removed dead cache optimization code that was causing truncated results (601 vs 11,171 songs)
- **Cleaner Codebase** - Removed invalidatePlaylistCache() and performLocalSearch() functions that depended on broken cache
- **Maintained Functionality** - All existing features (search, tooltip, media controls) remain intact and working
- All features from v7.1.3

### v7.1.3
- **Enhanced Menu Keyboard Shortcuts** - Updated Refresh and Search menu items to display keyboard shortcuts properly
- **Standard macOS UI** - Replaced inline shortcut text with proper NSMenuItem keyEquivalent and modifierMask
- **Consistent Menu Display** - Refresh menu item now shows ⌃⌥R shortcut on the right side like standard macOS apps
- **Improved Menu Integration** - Search menu item now shows ⌃⌥F shortcut on the right side like standard macOS apps
- **UI Guidelines Compliance** - Shortcuts now appear in proper location matching Quit menu item format
- All features from v7.1.2

### v7.1.2
- **Fixed Endless MPC Query Issue** - Implemented NSPopoverDelegate to handle external popover closure
- **Enhanced Tooltip Lifecycle** - Added popoverDidClose delegate method for proper timer cleanup
- **Resource Optimization** - Fixed issue where clicking menubar while tooltip showing caused endless MPC calls
- **Delegate-Based Cleanup** - Enhanced tooltip lifecycle management with delegate-based cleanup
- **Timer Management** - Ensures elapsed time timer stops regardless of how popover closes
- All features from v7.1.1

### v7.1.1
- **Tooltip Performance Optimization** - Enhanced tooltip updates to only run when MPD is in playing status
- **Smart Playback Detection** - Modified getCurrentElapsedTime to return playback status detection
- **Conditional Timer Updates** - Updated updateElapsedTime to stop timer when not playing
- **Status-Based Optimization** - Added playback state detection from MPD [playing] status output
- **Resource Efficiency** - Prevents unnecessary MPC queries during paused/stopped states
- All features from v7.1.0

### v7.1.0
- **Exclusive Global Hotkey System** - System-wide keyboard shortcuts that prevent other apps from seeing the key combinations
- **CGEventTap Integration** - Low-level event capture using Apple's official accessibility framework for true exclusivity
- **Conflict-Free Shortcuts** - Ctrl+Option+F (Search) and Ctrl+Option+R (Refresh) now work exclusively for MPD app
- **Accessibility Permission Integration** - Seamless permission handling with automatic prompts and clear user guidance
- **Event Consumption** - Selected key combinations are consumed before reaching other applications
- **Timeout Recovery** - Automatic re-enablement of event tap if system disables it for security
- **Menu Integration** - Context menu displays global shortcuts with proper notation (^⌥F, ^⌥R)
- **System Priority** - Hotkeys work from any application with highest system priority
- All features from v7.0.0

### v7.0.0
- **Advanced Search Interface** - Interactive floating search window with real-time MPD database search functionality
- **Visual Search Loading Indicators** - Animated braille spinners on both sides of search field during active searches
- **Smart Search Debouncing** - 10ms debounce timer with race condition protection for responsive search experience
- **Multi-word Search Support** - Intelligent search with multiple grep filters for complex queries
- **Search Result Navigation** - Keyboard navigation (↑↓) and mouse interaction with search results
- **Context Menu Integration** - Right-click context menus on search results with "Add to Queue" and playlist options
- **Queue Management from Search** - Direct song queuing from search results with visual priority indicators
- **Search Performance Optimization** - PID tracking and timeout protection for search operations
- **Clean Search UI** - Color-coordinated clear button matching placeholder text styling
- **Comprehensive Search Logging** - Detailed search timing and performance metrics for debugging
- All features from v6.1.1

### v6.1.1
- **Fixed Song Transition Display** - Resolved issue where "Mpd Queue Empty" was incorrectly shown during song transitions instead of new song details
- **Optimized Queue Length Check** - Skip queue validation during active playback to prevent race conditions during track changes
- **Improved Status Update Logic** - Queue empty detection now only runs when MPD is actually stopped, not during normal playback
- **Removed Debug Noise** - Cleaned up tooltip metadata debug messages for cleaner logs
- All features from v6.1.0

### v6.1.0
- **Enhanced Error Message Display** - Proper detection and display of multiline MPD error messages with scrolling support
- **Improved Error Detection** - Fixed detection of "ERROR:" and "MPD error:" messages appearing anywhere in MPD output, not just at the beginning
- **Performance Optimization** - Moved all MPD command execution to background threads to prevent UI blocking and spinning cursor issues
- **Timeout Protection** - Added timeout handling for all MPD operations to prevent infinite hangs on unresponsive servers
- **Asynchronous Status Processing** - Complete redesign of status update system for responsive UI during network operations
- **Consistent Error Message Scrolling** - Long error messages now use the same scrolling logic as song titles for better readability
- All features from v6.0.0

### v6.0.0
- **Interactive Media Player Tooltip** - Hover tooltip with real-time song info, progress slider, volume control, and media buttons
- **Enhanced Progress Control** - Custom red-colored progress slider with smooth seeking and real-time elapsed time updates
- **Advanced Tooltip Management** - Smart tooltip display only for song info (hidden during errors/empty states), graceful hover/exit handling
- **Volume Change Detection** - Added mixer events to MPD monitoring for external volume changes
- **Improved Album/Year Display** - Hide empty album/year labels instead of showing "Unknown" placeholders
- **Queue Empty Detection** - Display "Mpd Queue Empty" when no songs are loaded
- **Smooth Slider UX** - Enhanced seeking with Y-axis tolerance, pause updates during dragging, immediate calculated time display
- **Default Cursor Behavior** - Maintain arrow cursor throughout tooltip interface, no text selection cursors
- All features from v5.1.0

### v5.1.0
- **About Dialog** - Standard macOS about dialog with app icon, version info, and copyright
- **Server-Specific Media Controls** - Media keys now work correctly with remote MPD servers using `--host` and `--port` parameters
- **Enhanced Profile Support** - All MPD operations (playlists, media keys, status) properly target the selected profile's server
- **Improved Remote Server Compatibility** - Full functionality for non-localhost MPD profiles
- All features from v5.0.0

### v5.0.0
- **Complete Profile Management System** - Create, edit, delete, and switch between multiple MPD server profiles with CRUD interface
- **Intelligent Connection Handling** - Automatic connection testing, gentle error flashing, and 5-second retry mechanism for failed connections
- **Smart Profile Switching** - Tests connectivity before switching, shows target server status, handles graceful fallbacks when playing
- **Enhanced Status Display** - Shows hostname when server stopped, current song when playing, proper status updates per server
- **Profile Persistence** - Remembers and restores last used profile on app launch
- **Connection State Management** - Tracks connection states with visual feedback and automatic recovery
- **Server-Specific Operations** - All MPD commands properly target the selected profile's server with host/port parameters
- **Wake-from-Sleep Testing** - Automatically tests connections after screen unlock to ensure connectivity
- **Visual Profile Indicators** - ✓ checkmarks show current profile, context menus for easy management
- All features from v4.5.0

### v4.5.0
- **MPD Playlist Detection** - Enhanced playlist state detection using direct MPD protocol communication
- **Visual playlist indicators** - ♪ symbols now properly show for both specific playlists and music directory mode  
- **Improved MPD status parsing** - Uses `echo status | nc localhost 6600` for better `lastloadedplaylist` field detection
- **Smart playlist differentiation** - Automatically detects whether MPD is showing music directory or specific playlist on launch/refresh
- **Enhanced menu feedback** - Visual indicators update correctly based on detected playlist state
- All features from v4.4.0

### v4.4.0
- **Apple MediaPlayer Framework Integration** - Complete rewrite of media key handling using MPRemoteCommandCenter
- **Proper system priority** - Media keys now work with highest priority when app is installed (not just debug mode)  
- **Control Center integration** - Now Playing info appears in macOS Control Center and Lock Screen
- **Touch Bar support** - Full integration with MacBook Pro Touch Bar media controls
- **Siri compatibility** - Can be controlled via "Hey Siri" voice commands
- **No accessibility permissions required** - Uses official Apple APIs instead of low-level event taps
- **Better app cooperation** - Works alongside VLC, IINA, and other media apps properly
- **Enhanced Now Playing metadata** - Parses and displays Artist, Title, and Album information
- All features from v4.3.2

### v4.3.2
- **Selective media key interception** - Only intercepts playback controls (Play/Pause, Next, Previous)
- **Volume key passthrough** - Volume Up/Down and Mute keys now work normally with system
- **Improved media key handling** - No longer blocks all unknown media keys
- All features from v4.3.1

### v4.3.1
- **Code cleanup** - Removed unused playlist functionality
- **Simplified menu** - Streamlined context menu without playlist submenu
- **Performance improvement** - Removed playlist monitoring from MPD idle loop
- All features from v4.3.0

### v4.3.0
- **Automatic Login Items management** - Uses modern SMAppService API for startup management
- **macOS 13+ requirement** - Removed legacy compatibility for cleaner codebase  
- **Graceful fallback** - Shows manual setup instructions when automatic registration fails
- **Improved Launch at Startup toggle** - Now accurately reflects system state with proper error handling
- All features from v4.2.1

### v4.2.1
- **Project cleanup** - Removed old MenubarApp binaries and outdated files
- **Consistent naming** - All references updated from MenubarApp to MpdMacOS throughout the project
- **Updated build process** - Build instructions now use proper app bundle creation
- **Screen lock compatibility** - App no longer prevents macOS screen lock
- Pauses scrolling animation when screen locks to allow system idle detection
- Resumes animation when screen unlocks
- All features from v4.1

### v4.1
- **Improved app icon appearance** - Optimized icon sizing for better display in Finder
- Enhanced icon padding to fill more of the canvas while maintaining macOS design guidelines
- All features from v4.0

### v4.0
- **Context menu with Settings** - Right-click menu for app controls
- **Launch at Startup toggle** - Settings submenu with launch preference
- **Comprehensive debug output** - Detailed logging for all operations
- **Enhanced user feedback** - Clear instructions for manual setup steps
- **Improved app management** - Organized context menu with Quit option
- **App renamed to MpdMacOS** - Final branding with proper bundle naming
- All features from v3.0

### v3.0
- **Self-contained app bundle** - No external dependencies required
- Bundled `mpc` binary - Works without Homebrew installation
- **Visual status indicator** - Music note icon (♪) when MPD is stopped
- **Optimized menubar spacing** - Reduced padding for minimal space usage
- **Adaptive scrolling speed** - Slower scrolling for short text overflow (≤5 chars)
- **Smart state detection** - Proper differentiation between stopped vs paused
- Compact icon display with minimal margins
- All features from v2.0

### v2.0
- **Exclusive media key integration** - Complete control over macOS media keys
- System-level media key interception using CGEventTap
- Prevents Apple Music and other apps from responding to media keys
- Works with Play/Pause, Next, and Previous keys
- Requires accessibility permissions for exclusive control
- F-key fallback support (F7=Previous, F8=Play/Pause, F9=Next)
- All features from v1.0

### v1.0
- Initial release
- Displays current MPD song in the menubar
- Updates in real-time using MPD events
- Scrolling display for long titles
- Dynamic width adjustment based on content
- Text stops scrolling at last character
- Right alignment for shorter text
- Event-based MPD monitoring using `idleloop` instead of polling

## Installation

1. Clone the repository
2. Build using the build script: `./build-bundle.sh`
3. The app will launch automatically, or run: `open MpdMacOS.app`

You can also use the provided `rebuild.sh` script to rebuild and restart the application.

## Requirements

- **macOS 13.0 (Ventura) or later**
- MPD server running on localhost with default port
- **Accessibility permissions** (for exclusive media key control)

**Note:** No external dependencies required as of v3.0 - `mpc` is bundled within the app.

## Usage

The app automatically connects to your MPD server and displays the currently playing song in the menubar. The display updates automatically when the song changes.

When a song title is too long to fit in the menubar, it will automatically scroll. Short titles are displayed without scrolling.

### Context Menu (v4.0)

The app now includes a right-click context menu with:
- **Server information** - Shows connected MPD server (localhost)
- **Settings submenu** - Contains Launch at Startup toggle
- **Quit option** - Clean app termination

### Launch at Startup (v4.0)

Toggle launch at startup preference through Settings > Launch at Startup. When enabled, provides instructions for manual setup in System Preferences > Users & Groups > Login Items.

### Visual Indicators (v3.0+)

- **Playing/Paused:** Song title with artist and album info
- **Stopped:** Music note icon (♪) to indicate app is running
- **Adaptive Display:** Minimal padding and smart scrolling based on text length

### Media Key Control (v2.0+)

The app takes exclusive control of your Mac's media keys (Play/Pause, Next, Previous), preventing Apple Music and other applications from responding to them. This requires granting accessibility permissions when first launched.

**Fallback Keys:** If accessibility permissions aren't granted, you can still control MPD using:
- F7: Previous track
- F8: Play/Pause  
- F9: Next track
