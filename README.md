# Window Shell

A learning-focused desktop shell for Hyprland, built with
[Quickshell](https://quickshell.org/). The project aims to provide a focused top
panel and progressively add the everyday controls expected from a desktop
environment.

## Vision

The shell will provide a consistent place to see the current desktop state,
move between workspaces, manage common system services, review notifications,
and control the session.

The initial interface is informed by existing Wayland panels, but no screenshot
or existing shell is the specification. Visual and interaction decisions will
be developed as the project grows.

## Planned capabilities

- A top panel with the focused-window title, clock, and workspace selector.
- System-tray icons with application-provided interactions and context menus.
- Audio output and volume controls.
- Bluetooth device controls.
- Notification toasts and a notification center.
- Shutdown, restart, sleep, and locking controls.
- A lock screen and, later, a login environment.

## First milestone: core panel

Build a usable single-monitor panel containing:

- A panel frame attached to the top of the screen.
- The focused Hyprland window title.
- A clock.
- Workspace buttons for workspaces 1 through 5.
- A visible effect that distinguishes the active workspace.
- The ability to select a workspace from the panel.

The panel reserves desktop space rather than covering application windows. When
no window is focused, the window-title area remains blank.

The milestone is complete when the shell starts without errors and each element
updates correctly during ordinary Hyprland use.

## Initial boundaries

- Hyprland is the first supported compositor.
- The first version targets one monitor at a time.
- Multi-monitor behavior is deferred until it can be tested with appropriate
  hardware.
- This is a top panel, not a Windows-style running-application taskbar.
- Application icons such as Discord and Steam belong to the system tray.
- Notification history must survive shell restarts, logout, and reboot until the
  user dismisses it.

## Requirements

Current requirements:

- A Wayland session running Hyprland.
- Quickshell.

Later capabilities will introduce additional system-service dependencies such
as PipeWire, BlueZ, PAM, and Greetd. Exact versions and installation steps will
be recorded after they are tested.

## Running the shell

Run the configuration entry point from the repository root:

```sh
qs -p shell.qml
```

## Project structure

```text
.
├── AGENTS.md          # Mentoring guidance for coding agents
├── docs/
│   ├── DECISIONS.md   # Agreed boundaries and unresolved questions
│   └── ROADMAP.md     # Incremental development milestones
├── README.md          # Project overview and current scope
└── shell.qml          # Quickshell entry point
```

## Planning

- [Development roadmap](docs/ROADMAP.md)
- [Decision log](docs/DECISIONS.md)
