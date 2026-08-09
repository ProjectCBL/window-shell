# Development Roadmap

This roadmap organizes the shell into small, observable outcomes. Only the core
panel milestone is currently committed to a detailed scope. The order and scope
of later milestones may change as the project develops.

## Milestone 0: runnable shell

**Outcome:** Establish the smallest Quickshell configuration that can be started
and observed during development.

- Use `qs -p shell.qml` as the local Quickshell launch command.
- Confirm that `shell.qml` loads without errors.
- Record any additional environment requirements discovered during testing.

## Milestone 1: core panel

**Outcome:** Provide a useful top panel for a single Hyprland monitor.

- Create a panel frame attached to the top edge.
- Reserve desktop space so application windows do not extend behind the panel.
- Display the focused Hyprland window title.
- Leave the window-title area blank when no window is focused.
- Display the abbreviated weekday, abbreviated month, and 12-hour time with
  minutes and an AM/PM indicator.
- Always display workspace selectors numbered 1 through 5.
- Place a rounded rectangle behind the active workspace number.
- Animate the rectangle toward the newly active number when workspaces change.
- Use the normal number color for the rectangle and the panel background color
  for the active number, keeping the number legible.
- Allow each workspace selector to activate its corresponding workspace.
- Handle the absence of a focused window without displaying stale information.

**Done when:**

- The panel starts without QML errors.
- The clock updates correctly.
- The focused-window title follows Hyprland focus changes.
- Workspaces 1 through 5 remain visible.
- The highlight follows the active workspace.
- Selecting a workspace changes to it.
- The indicator moves to the selected workspace without hiding its number.

## Milestone 2: audio status and controls

**Outcome:** Show the current output volume and provide a small control surface.

- Read audio state through PipeWire.
- Show volume and mute state in the panel.
- Open a volume control widget from the panel.
- Change output volume and mute state.

## Milestone 3: system tray

**Outcome:** Display background application indicators such as Discord and
Steam.

- Render the current system-tray items and their supplied icons.
- Invoke each item's primary action where supported.
- Display application-provided menus at the correct panel location.
- Handle tray items appearing and disappearing at runtime.

## Milestone 4: session controls

**Outcome:** Provide deliberate access to common session and power operations
from the left corner of the panel.

- Place a session-menu icon in the left corner of the panel.
- Reveal an anchored options panel with a sliding transition when the icon is
  selected.
- Provide sleep, restart, and shutdown actions.
- Add confirmation where an accidental action would be disruptive.
- Treat the supplied screenshots as interaction references rather than a visual
  specification.

## Milestone 5: Bluetooth controls

**Outcome:** Inspect and manage common Bluetooth device state from the shell.

- Show adapter state.
- List relevant devices.
- Connect and disconnect devices.
- Expose useful connection feedback and failures.

## Milestone 6: notifications

**Outcome:** Deliver temporary notification toasts and durable notification
history.

- Receive desktop notifications.
- Show each new notification as a temporary toast.
- Hide the toast without dismissing the underlying notification.
- Expose a panel indicator that opens the notification center.
- List notifications that have not been explicitly dismissed.
- Allow individual dismissal and an intentional clear-all action.
- Persist eligible notification history across shell restarts, logout, and
  reboot.
- Define how transient and sensitive notifications are handled before enabling
  persistence.

## Milestone 7: lock screen

**Outcome:** Secure the active session with an authentication-backed lock
screen.

- Cover the active display while locked.
- Authenticate through PAM.
- Prevent ordinary dismissal or bypass.
- Verify failure and recovery behavior before relying on it.

## Milestone 8: login environment

**Outcome:** Explore a Greetd-backed login interface as a separately launched
surface within the repository.

This milestone remains intentionally late because a login environment operates
outside the normal user session and has different security and failure modes.

## Deferred work

- Multi-monitor panel behavior.
- Per-monitor workspace and focused-window state.
- Per-monitor configuration.
- Support for compositors other than Hyprland.
