# VaultTracker

A [MUSHclient](https://www.gammon.com.au/mushclient/) plugin for [Discworld MUD](https://discworld.starturtle.net/)
that remembers what's inside your vaults and shows them in a tabbed miniwindow.

Look inside a vault container once and VaultTracker records its contents; from then on you
can browse, search, and gauge fullness of all your vaults from anywhere, across sessions.

![Requires CowBar](https://img.shields.io/badge/requires-Quow's%20CowBar-orange)

## Features

- **Automatic capture** — look in a registered vault's container and the contents are
  parsed (individual items) and saved. Multi-line item lists are handled.
- **Room-aware** — vaults are keyed by GMCP room id, so identically named containers in
  different rooms are separate vaults.
- **Container lock** — each vault binds to its own container's phrasing after the first
  capture, so looking in your backpack in the vault room won't overwrite the record.
- **Tabbed miniwindow** — one tab per vault with a color-coded fullness dot
  (green = empty → red = completely full), draggable, resizable, mouse-wheel scrolling,
  tabs wrap to multiple rows. Items sorted alphabetically (ignoring the leading quantity word).
- **Fullness display** — the container's fullness line is shown color-coded above the contents.
- **Search** — `vault find <text>` searches every recorded vault at once.
- **Persistent** — contents, window position/size, and settings survive restarts
  (MUSHclient plugin saved state).

## Requirements

- MUSHclient 4.84+
- [Quow's CowBar / minimap plugin](https://quow.co.uk/minimap.php) — VaultTracker gets its
  room information from CowBar's GMCP rebroadcast.
- CowBar's **"Re-Broadcast GMCP Data"** option must be ON: right-click the minimap and tick
  it (one-time setting; VaultTracker warns you if it looks disabled).

## Installation

1. Download `VaultTracker.xml` and place it anywhere (e.g. next to Quow's plugins).
2. In MUSHclient: **File → Plugins → Add**, select `VaultTracker.xml`.

## Usage

Stand in the room containing a vault, then:

```
vault register <name>     register the room you are standing in as a vault
```

Then simply look in the vault's container (e.g. `l drawer`). The first capture locks the
vault to that container and records everything.

```
vault list                list registered vaults (lock status, counts, timestamps)
vault show [name]         print a vault's contents to the output window
vault find <text>         search all vaults for an item
vault window              show/hide the miniwindow
vault unlock [name]       re-bind a vault to a different container
vault forget <name>       unregister a vault
vault help                command overview
```

## License

MIT
