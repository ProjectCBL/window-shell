# Decision Log

This file records project decisions and their reasons. It is not an immutable
specification: revise a decision when new evidence or testing justifies it.

## Current decisions

### Target Hyprland first

Hyprland is the initial compositor target. This permits the project to use and
learn from Quickshell's Hyprland integration instead of designing a generic
compositor abstraction prematurely.

### Build a top panel, not an application taskbar

The primary surface is a Wayland/Hyprland top panel. It reports desktop and
system state; it does not list every running application or restore application
windows like a traditional Windows taskbar.

### Treat visual references as references only

Screenshots and existing bars may communicate useful layout ideas, but they do
not define the required appearance or behavior of this shell.

### Show fixed workspace selectors 1 through 5

The core panel always displays workspace buttons numbered 1 through 5. The
currently active workspace receives a visible effect, and selecting a button
activates that workspace.

The active indicator is a rounded rectangle behind the workspace number. It
uses the normal number color, while the active number changes to the panel
background color. When the active workspace changes, the rectangle moves toward
the corresponding number instead of the numbers moving with it.

### Reserve desktop space for the panel

The panel reserves space at the top of the desktop rather than overlaying
application windows.

### Leave an unfocused window title blank

When Hyprland has no focused window, the focused-window title area displays no
fallback label.

### Use an abbreviated 12-hour clock format

The panel clock displays the abbreviated weekday, abbreviated month, and time
with minutes and an AM/PM indicator.

Format: `{weekday} {month} {hh:mm AM/PM}`

### Target one monitor initially

The first implementation targets one monitor at a time. Multi-monitor support is
deferred because it cannot currently be tested on the developer's hardware.

### Treat background application icons as system-tray items

Applications such as Discord and Steam appear through the system tray. Their
icons, primary actions, and contextual menus come from the application's tray
item rather than a model of open Hyprland windows.

### Separate toast visibility from notification dismissal

A notification toast may disappear while its notification remains available in
the notification center. Only an explicit user dismissal removes a retained
notification.

### Persist notification history

Eligible notifications remain available across shell restarts, logout, and
reboot until the user explicitly dismisses them. This requires durable storage;
in-memory notification tracking is insufficient.

The exact stored fields, handling of transient notifications, and protection of
sensitive content are deferred until notification-center design begins.

### Place session controls in a left-corner menu

A clickable icon in the panel's left corner reveals an anchored panel with a
sliding transition. It provides sleep, restart, and shutdown actions. The
supplied menu screenshots are interaction references, not appearance targets.

### Follow the agreed milestone order

After the runnable-shell foundation, the current order is core panel, audio,
system tray, session controls, Bluetooth, notifications, lock screen, and login
environment.

## Notification terminology

A **transient notification** is marked by its sending application as temporary
and unsuitable for persistence. It commonly represents short-lived state that
does not need to remain in notification history. The shell's exact treatment of
these notifications remains deferred until the notification-center milestone.

## Open questions

- Which notification fields should be stored on disk?
- Should transient notifications ever enter history?
- How should sensitive notification content be identified and protected?
- Which icon and precise animation should the session menu use?
- When multi-monitor work begins, should every monitor have a screen-aware panel
  or should panel placement be configurable?
