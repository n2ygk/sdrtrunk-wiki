# Primary Application Window
The following sections detail how to use the features available in the sdrtrunk primary application window.

<!-- TOC -->
* [Primary Application Window](#primary-application-window)
* [Overview](#overview)
* [Menus](#menus)
* [Spectral & Waterfall Display Panels](#spectral--waterfall-display-panels)
  * [Spectral Display Panel](#spectral-display-panel)
    * [Spectral Display Context Menus](#spectral-display-context-menus)
  * [Waterfall Display Panel](#waterfall-display-panel)
    * [Waterfall Context Menu](#waterfall-context-menu)
  * [Zooming - Spectral and Waterfall Display](#zooming---spectral-and-waterfall-display)
* [Audio Playback Panel](#audio-playback-panel)
  * [Audio Playback Panel - Context Menu](#audio-playback-panel---context-menu)
* [Tabbed Views](#tabbed-views)
  * [Now Playing](#now-playing)
  * [Map](#map)
  * [Tuners](#tuners)
  * [Playlist Editor](#playlist-editor)
* [Streaming Status Panel](#streaming-status-panel)
<!-- TOC -->

# Overview
The sdrtrunk primary application window is composed of the following sections:
* **Spectral Display** - displays the frequency content of the currently selected tuner
* **Waterfall** - displays a running history of the frequency content from the spectral display.
* **Audio Playback** - displays in-progress call audio playback
* **Tabbed Views** - a set of tabbed views:
  * **Now Playing** - a table of channels currently decoding with a selected channel activity detail panel
  * **Map** - a map view for displaying decoded mobile radio GPS locations
  * **Tuners** - view of tuners and tuner control editors
  * **Playlist Editor** - quick-access button to open the [Playlist Editor](Playlist-Editor)
* **Streaming Status** - status of audio streaming call activity

![Image of the primary application window with highlighting of the main functional sections](images/application_overview.png "Application Overview")

# Menus
The following menus are available at the top of the primary application window.
* **File** Menu
  * **Exit** - shutdown the application.
* **View** Menu
  * **Playlist Editor** - opens the [Playlist Editor](Playlist-Editor) window
  * **User Preferences** - opens the [User Preferences](User-Preferences) editor.
  * **Icon Manager** - opens the [Icon Manager](Icon-Manager) editor.
  * **Logs & Recordings** - opens a system file explorer to the sdrtrunk applicaton directory where the log files and 
recordings are stored
  * **Tuners** - presents a list of system tuners allowing you to select a specific tuner for display in the Spectral 
Display window.
  * **Disable Spectrum & Waterfall** - disables the Spectral Display and Waterfall and pauses FFT calculations.  Use 
the **View >> Tuners** menu to select a tuner and restart the displays.
  * **Show Streaming Status** - toggle button to turn on or off the streaming status panel at the bottom of the primary 
application window.
* **Screen Capture** Menu - button to take a screenshot of the primary application window.  Screenshots are stored in the 
sdrtrunk screenshots directory.  Use the **View >> Logs & Recordings** menu item to open a file explorer to the
sdrtrunk directory and access screenshots.

# Spectral & Waterfall Display Panels
## Spectral Display Panel
The spectral display panel provides a zoomable view of the frequency content from the currently selected tuner.  On 
startup, the application automatically selects the first tuner for display, unless the user has disabled the 
spectral and waterfall displays.  

The spectral display overlays the frequency spectrum with channel overlays for each decoding channel that you define in 
the playlist manager as well as dynamically allocated traffic channels when decoding trunked radio systems.  The cursor 
also displays the frequency value and current zoom levels when you hover your mouse over the spectral display areas.

### Spectral Display - Context Menus
![Image of the context menu that appears when you right-click on the spectral display panel](images/spectral_display_context_menu.png "Spectral Display Context MenuA")


* **Channels** Menu - displays a list of channels currently under the cursor area and presents menu option(s) to display 
each channel in the [Playlist Editor](Playlist-Editor)


* **Color** Menu - presents submenu options for configuring the color setting for each of the features displayed in the 
Spectral Display and Waterfall panels.  A color chooser is presented for each submenu.  These settings are remembered
across application restarts.
  * **Channel** - channel overlay for a channel that is not currently enabled for processing.
  * **Channel Processing** - channel overlay color for a channel that is currently enabled for processing.
  * **Channel Selected** - channel overlay color for a channel that is currently selected in the Now Playing table.
  * **Cursor** - color for the cursor and frequency/zoom details
  * **Line** - color for frequency reference line details
  * **Background** - background color for the spectral display
  * **Gradient Bottom** - foreground color of the frequency content gradient.
  * **Gradient Top** - foreground color of the frequency content gradient.


* **Display** Menu - provides submenu options for configuring the spectral display.
  * **Averaging** - controls the averaging of successive FFT calculation results.  A setting of 1 turns off 
averaging and presents a dynamically changing spectral display.  Values higher than one indicate the quantity of FFT
calculation results that are averaged together before display.  Higher values present a more stable frequency content
display, but may not be dynamic enough to display very short duration signals.
  * **Channel** - controls the display of channel overlays.  When you have a wide bandwidth tuner displayed with many 
channels, the display can become cluttered.  Use these menu options to manage this display.
    * **All** - displays all channel overlays.
    * **Enabled** - only displays channels that are enabled for processing.
    * **None** - turns off display of channel overlays.
  * **FFT Width** - controls the size of the FFT used for calculating the frequency content from the currently selected 
tuner.  Smaller values require less processing power but provide very coarse frequency resolution.  Higher values provide
finer-grained frequency resolution but also require more processing power.
  * **Frame Rate** - controls the number of FFT calculations per second.  Setting this value lower will decrease
processing requirements, but the Spectral Display will be slow to refresh.  Setting this value higher will update the 
spectral display more quickly, but will also require more processing.
  * **Window Type** - configures the window used in the FFT calculation.  Different windows can affect the FFT 
calculation in different ways with some windows producing a 'splattering' effect where higher strength
signals splatter across the frequency spectrum.  Experiment with each window setting to find one that you prefer.
  * **Smoothing** - controls the averaging of frequency bins across the FFT results.  Turning on smoothing will flatten
out the frequency content and can reduce the peak values of signals while smoothing the signals and noise floor into a 
softer appearance. Smoothing is turned off by default.  The submenu options control the averaging algorithm
that is used and the number value range controls how many frequency bins are averaged together.


* **Zoom** Menu - allows you to zoom the spectral and waterfall displays.  


* **Disable Spectrum & Waterfall** Menu - a toggle button controlling FFT calculations and the
spectral and waterfall displays.  When disabled, both displays show empty frequency content and a label 
indicating **DISABLED - Right Click to Select a Tuner**.  Use the context menu to select a tuner and 
enable FFT calculations and spectral and waterfall displays.


* **Show - TUNER** Menu - an optional menu item that appears for each tuner that can be displayed in the 
spectral and waterfall displays.  Use one of the show tuner menu options to reenable display of frequency content
after you have disabled the spectral and waterfall displays.

## Waterfall Display Panel
The waterfall panel displays a running history of the frequency content from the spectral display.

### Waterfall - Context Menus
![Image of the context menu that appears when you right-click on the waterfall panel](images/waterfall_context_menu.png "Waterfall Context MenuA")

* **Pause** Menu - toggles on/off pausing of the waterfall display.  This allows you to pause the display to inspect the frequency
values for signals that have appeared in the recent past history so that you can configure a decoding channel for the 
correct frequency.  


* **Color / Display / Zoom / Disable Spectrum & Waterfall** Menus - these are the same menu options that are available in the Spectral Display context menu (see above).

## Zooming - Spectral and Waterfall Display
* **Zoom** - use your mouse scroll wheel to zoom in and out of the spectral and waterfall displays.  The panels zoom
about the frequency center currently under the mouse so that you can hover over a signal and quickly zoom in on that
signal.  A zoom control appears at the bottom of the waterfall display panel to show the zoom size and the location of 
the zoomed area relative to the unzoomed frequency spectrum.


* **Drag To Scroll** - use the mouse left-click drag to scroll across the zoomed-in displays and change the currently
visible portion of the frequency spectrum.

# Audio Playback Panel
The audio playback panel displays the current audio playback of either a single (mono) channel to both speakers or two 
channels (stereo) with separate call audio in each of the left and right audio channels.

* **Mute Button** - the speaker icon controls muting of audio playback.  Green indicates the audio is unmuted.  Red
indicates the audio is muted.  Click the speaker icon to toggle between muted and unmuted.

* **MONO Panel** - displays the current call audio information when configured for a single playback channel.


* **LEFT Panel** - displays call audio details for the left audio channel when configured for stereo playback channels.


* **RIGHT Panel** - displays call audio details for the right audio channel when configured for stereo playback channels.

## Audio Playback Panel - Context Menus
Right-click anywhere along the audio playback panel to access the context menu.
![Image of the context menu that appears when you right-click on the audio playback panel](images/audio_playback_context_menu.png "Audio Playback Panel - Context Menu")

* **Configure** - button to open the [User Preferences](User-Preferences) editor and configure the mixer or sound 
card to use for audio playback.  Each sound card or mixer device can be selected and configured for mono or stereo 
audio playback, when supported by the audio device.


* **Channel: MONO** Menu - presents submenu options for configuring the MONO playback channel.
  * **Mute** Menu - mutes just this channel.  When muted, a red 'R' appears in the channel panel.
  * **Volume** - controls audio volume for just this channel.


* **Channel: LEFT** Menu - presents submenu options for configuring the LEFT playback channel with the same Mute and 
Volume submenu options.


* **Channel: RIGHT** Menu - presents submenu options for configuring the RIGHT playback channel with the same Mute and
  Volume submenu options.

# Tabbed Views

## Now Playing

## Map

## Tuners

## Playlist Editor

# Streaming Status Panel