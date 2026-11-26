# The Sonar Room

**A game of echolocation for Android. You are blind. Sound is sight.**

The screen is black. You have no map, no torch, no view of the room around you.
What you have is a ping: a sonar wave that expands from your body, lights up the
walls it touches, then fades. Everything you know about the world arrives that
way — or through your ears.

A ping is a flashlight, a map update, and a scream for attention at the same
time. That trade is the whole game.

> Short runs. Clean losses. Headphones strongly recommended.

<!-- TODO: drop 2–3 landscape screenshots or a short GIF here -->

## At a glance

| | |
| --- | --- |
| **Players** | 1 solo · 2–10 over a local network |
| **Orientation** | Landscape only |
| **Network** | Local Wi-Fi or phone hotspot. No internet, no accounts, no server |
| **Assets** | None — walls are canvas strokes, every sound is synthesized at runtime |
| **Install size** | Small. Minified, no art or audio bloat |
| **Best time** | Stored locally on the device |

## Features

- **Solo** — find three keys, open the door, escape before the thing in the dark finds you. The monster sleeps for eight seconds, then wanders, investigates your pings, and chases if you get close. It gets faster with every key you take.
- **Two-player hunt** — survivor vs hunter on the same maze. Both are blind. The survivor's clean ping reveals the maze to *both* players; the hunter's echoclick is a smaller, jagged reveal that gives away the hunter. A catch ends the run.
- **Pack runs (3–10 players)** — shared key pool, multiple survivor bodies, Echo-Revive (a downed teammate can be revived once), scaled maps, up to four colored doors, and up to five hunters with Stalker / Listener / Warden kinds.
- **Deterministic maps** — the seed is picked once and every device builds the same maze locally. Nothing but the seed crosses the wire.
- **Everything is generated** — no art assets, no audio files. The bundled typefaces (Styro, Technor, Teko) are the only static resources.
- **Local best time** — solo escapes are timed and stored on the device. Hunt results never touch it.

## Install

Requirements: an Android phone or tablet. A few MB of free space.

1. Download the latest `sonar-room-release.apk` from Releases.
2. Open it on the device (allow "Install unknown apps" for your browser or file manager), or install over adb:

   ```bash
   adb install -r sonar-room-release.apk
   ```

## How to play

- **Move** — drag inside the on-screen pad. It sits where you put it; change its position and size in **Settings**.
- **Ping** — tap anywhere outside the pad. A white ring expands from you, reveals walls, keys, and doors, then fades within about three seconds. Knowledge decays; memory is the map.
- **Solo** — collect three keys, find the door, step through it. The door unlocks automatically when the third key is taken.
- **Hunt** — the survivor collects three crimson and three jade keys and holds still near a door to work its lock. The hunter follows the survivor's own pings and patrols the doors. A catch ends the run.
- **Pack run** — touching an open door does nothing; you must hold the **EXIT** chip near it. Leaving others behind is a deliberate act, not a quirk.

## Multiplayer

No room service, no internet dependency. One device hosts, the rest join over the same network.

1. Put every device on the same Wi-Fi or Android hotspot.
2. One player **creates a room** and picks a side. The host listens on TCP.
3. Guests see nearby rooms over UDP  and join with one tap — or enter `ip:port` manually if broadcast is filtered on your network.
4. Everyone presses **READY**; the host presses **START**.
5. Two players → classic 1-hunter/1-survivor hunt. Three to ten → pack run.

A room holds up to **10 players**. If someone drops mid-run, their body is removed and the rest keep playing. A silent link (5 seconds) returns the affected devices to the lobby — there is no AI takeover and no reconnect.

## Tips

- **Ping less than you think.** A ping every cooldown is a beacon. Ping to answer a specific question, then move on the answer.
- **Move after pinging.** The monster investigates the ping's origin, not you.
- **Use the thuds.** The nearest walls thud first and loudest — your close-range collision warning in a corridor you haven't lit yet.
- **Hunt survivors:** your ping is the hunter's map. Use it for route decisions and lock approaches, not for comfort.
- **Hunt hunters:** let the survivor light the map, patrol the doors, and listen for the lock blips. A stationary target is the best information in the game.

## What's not in this build

Deliberately small:

- No items, decoys, or abilities (planned).
- No voice chat or emotes — communication is the game's own noise.
- No difficulty selector; the seed and the monster's key-driven speed are the difficulty.
- No pause during a live run. Back opens options; network hunts keep ticking underneath so the other player is never held up.
- No online leaderboard. Solo best time is local only.

## Credits

- **Type:** Styro Black and Technor (FFL), Teko (OFL). Notices in `licenses/`.

## License

The Sonar Room is **free to play**. It is licensed under the **PolyForm Noncommercial License 1.0.0** (see the `LICENSE` file for full terms).

This means you are free to download, play, share, and modify the game for any **noncommercial purpose**. However, all commercial rights are strictly reserved by the author. You may not sell the game, bundle it into a commercial product, or otherwise use it for commercial gain without written permission. 

This applies to the game as a whole (design, rules, text, source code, and compiled binaries); the bundled typefaces remain under their own respective licenses as noted in `licenses/`.
