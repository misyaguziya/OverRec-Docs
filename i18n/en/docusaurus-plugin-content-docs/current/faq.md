---
sidebar_position: 7
title: FAQ
description: What to check when something does not work, and how to report a bug.
---

# FAQ

## The panel does not appear on my wrist {#no-panel}

- Check that SteamVR and OverRec are running. They work together when **SteamVR** at the bottom right of the PC settings window says "Linked".
- If it stays "Not running", start SteamVR and wait a few seconds. If nothing changes, restart OverRec.
- Turn your wrist toward your face, as if looking at a watch. The panel appears when its face is turned to yours.
- If you lost it after moving it, press **"Back to wrist"** in "VR controls" in the PC settings window.
- With the panel made small, only [the small sign](/customize#mini) appears. Point at it and press to bring the panel back.
- It does not work when you play without SteamVR (VDXR or Meta's OpenXR runtime).
- If the log says "Shared IPC Namespace Unavailable (310)", [an app is running as administrator](#admin).

## SteamVR is running, but it stays "Not running" (error 310) {#admin}

When the log says `Not connected to SteamVR: Shared IPC Namespace Unavailable (310)`, only one of OverRec and SteamVR is running as administrator.
Windows keeps apps running as administrator and ordinary apps from talking to each other, so OverRec cannot connect to SteamVR.

Run them all without administrator rights.

1. Right-click OverRec, SteamVR and the app that starts SteamVR (Virtual Desktop Streamer and so on) → "Properties" → "Compatibility", and uncheck **"Run this program as an administrator"**.
2. Restart the PC, start SteamVR the usual way, then start OverRec.

Task Manager shows how they are running. In the "Details" tab, right-click a column heading → "Select columns" → **"Elevated"**. When both `OverRec.exe` and `vrserver.exe` say "No", they match.

## It does not connect to OBS {#no-obs}

When **OBS** at the bottom right of the PC settings window says "Not connected", the log in "Troubleshooting" says why.

- Check that OBS Studio is running.
- Check that "Enable WebSocket server" is checked in OBS's "Tools" → "WebSocket Server Settings".
- Check that the port and password are the same as in OBS's window. **"Test connection"** in "Connection" tries them.
- OBS Studio older than 28 does not work.

When OBS is started later, OverRec connects by itself in a few seconds.

## "Save replay" does not work {#no-replay}

- When the button says "Start replay", the replay buffer is stopped. Pressing it starts it.
- When it says OBS's replay buffer is off, turn it on with **"Set up in OBS"** in "OBS" in the PC settings window.
- If it still does not work, restart OBS.
- See the saved files with "OBS" → "Save location" → "Open folder".

## "Chapter" cannot be pressed {#no-chapter}

Chapters can be added only while recording, with OBS 30.2 or later. If pressing it gives an error, set OBS's recording format to Hybrid MP4.

## The mic button says "No mic" {#no-mic}

OBS has no audio input, or the chosen one was not found. Choose it again in "OBS" → "Mic input" in the PC settings window.

## The game reacts when I press the panel {#game-input}

Turn on **"Enable global input from overlays"** in SteamVR's settings.
Even then, the stick reaches the game while you hold the panel.

## A bound button does nothing {#bindings}

- Check in SteamVR's bindings window that OverRec's bindings are the ones in use.
- Check that OBS is connected.

## Icons look different, or text is missing {#icons}

On Windows 10, some icons have a different shape. If no text shows at all, please [report it](#report).

## OverRec quits when SteamVR does {#auto-quit}

That is the default. To keep it running, turn off "General" → "Quit with SteamVR".

## I want to start the settings over {#reset}

Open the folder with "Troubleshooting" → "Settings folder" → "Open folder", quit OverRec, then delete that folder. The next start begins with the first-run guide.
The OBS password stays in Windows Credential Manager. To change it, enter it again in "Connection".

## An OverRec entry is left in SteamVR {#leftover}

Uninstalling while SteamVR is stopped can leave OverRec in SteamVR's list of apps to start.
Turn it off in SteamVR's settings under "Startup / Shutdown".

## Bug reports and requests {#report}

They are taken on [GitHub Issues](https://github.com/misyaguziya/OverRec-Docs/issues/new/choose). Choose "Bug report" or "Feature request".

Please add these to a bug report:

- OverRec's version (bottom left of the PC settings window)
- Your VR headset and how it is connected (Steam Link, Virtual Desktop and so on)
- OBS Studio's version
- What you did, and what happened
- The log ("Troubleshooting" → "Log" → "Copy"), and `error.log` from the settings folder if there is one

:::caution
Issues is a public place. The log may show where files are saved (paths with your user name). Remove your user name before pasting it.
:::

If you don't have a GitHub account, a message on BOOTH is fine too.
