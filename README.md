# Penguin Runner – Know Your Distro

A fast, canvas‑based runner game where you dodge and collect Linux distro tiles while learning their families. Built as a single `index.html` file with no external frameworks.

## Overview
- Runner gameplay with parallax background, weather, and animated penguin.
- Distros appear as tiles with logos; correct picks increase score, wrong ones reduce lives.
- Two modes: Rapid (3 rounds, fixed teams) and Infinite (endless, switchable teams).
- Map overlay, pause overlay, and a Rapid finish screen with totals and per‑round scores.

## Modes
- Rapid
  - Play three teams, 10 lives per team; no mid‑round switching.
  - After three rounds, shows a finish screen with total and per‑round scores.
  - Code: `index.html:238–257`, finish overlay logic at `index.html:818–839`.
- Infinite
  - Play indefinitely; you can switch teams anytime.
  - Tracks non‑persistent run total and a cached high score in `localStorage`.
  - Code: `index.html:258–274`, high score handling in collisions `index.html:929–931`.

## Controls
- Jump: `Space`, `ArrowUp`, `W`, or click/tap (`index.html:349–350`).
- Move: `A/Left` and `D/Right` while on ground (`index.html:353–357`, `index.html:889–893`).
- Pause: `P` or click pause (`index.html:389–398`).
- Reset: `R` (`index.html:353–357`).
- Map: hold `M` to view distro map and pause (`index.html:363–386`).
- Start: `Enter` from the launch screen (`index.html:401–407`).
- Secret: hold `H` 3s then enter password `ecoholic` to enable showcase mode (`index.html:409–431`).

## Scoring and Lives
- Correct pickup: `+50` (`SCORE_GOOD`).
- Wrong pickup: `-20` (`SCORE_BAD`).
- Lives per team: `10` (`LIVES_PER_TEAM`).
- Max wrong per team: `10` triggers team change (`MAX_WRONG_PER_TEAM`).
- Speed ramps with score and caps at `2×` (`index.html:928–939`).

## Teams and Distros
- Major teams: Debian, Red Hat, Arch, Slackware, Gentoo (`index.html:221–226`).
- Derivatives configured in `TEAMS` (`index.html:145–151`).
- Icon paths configured in `ICONS` (`index.html:455–471`).

## Visual Parameters
- Gravity: `GRAVITY = 1.10` (`index.html:165`).
- Jump velocity: `JUMP_VELOCITY = -30` (`index.html:166`).
- Air drift: `AIR_DRIFT = 0`, `AIR_DRIFT_FRICTION = 0.4` (`index.html:167–168`).
- Base scale: `SCALE = 0.75` (`index.html:171`).
- Penguin scale: `PENGUIN_SCALE = SCALE + 0.3` (`index.html:172–173`).
- Distro tile scale: `TILE_SCALE = (SCALE - 0.2) * 1.3` (`index.html:173`).
- Tile size basis: `TILE_SIZE = 96` (`index.html:175`).
- Spawn pacing: `GAP_BASE = 420`, `GAP_RANGE = 220`, `PAIR_GAP = 240` (`index.html:178–180`).
- Walk bounds: 10%–80% screen width (`index.html:296–300`).

## Jump System
- Ground jump uses `JUMP_VELOCITY` (`index.html:342–348`).
- Mid‑air jump: configurable secondary jump when airborne.
  - `MAX_AIR_JUMPS = 1` additional jump (`index.html:168–169` additions).
  - `JUMP_SECONDARY_SCALE = 0.5` scales secondary jump strength.
  - Reset on landing (`index.html:908–909`).
  - Modify these values to tune difficulty.

## Overlays
- Launch overlay with mode details (`index.html:120–134`).
- Team selection overlay (`index.html:96–103`).
- Map overlay (`index.html:105–108`), holds `M` to view.
- Pause overlay (`index.html:111–117`), toggled with `P`.
- Rapid finish overlay with emoji and gradient title (`index.html:139–148`).

## HUD and UI
- Team logo shown next to the team label (`index.html:74–81`, `index.html:813–816`).
- Mode radio toggles (`index.html:84–91`) confirmed via prompt (`index.html:277–294`).
- Team menu with icons (`index.html:843–872`).

## Audio
- Cheer on correct, sad on wrong; simple oscillator tones (`index.html:502–511`).
- Primed on first user click (`index.html:513`).

## Weather and Background
- Weather rotates among Clear/Snow/Overcast (`index.html:553–563`).
- Parallax icy mountains and snow particles (`index.html:565–602`).

## Development Notes
- Single file app; open `index.html` in a modern browser.
- Assets expected in paths:
  - `icons/*.png` for distro/team logos.
  - `penguin-sprite.png` optional sprite (disabled by default).
  - `distro-map.jpg` for map overlay.
- No build step. To tweak gameplay, adjust constants listed above.

## Customization Tips
- Change difficulty: tune `GRAVITY`, `JUMP_VELOCITY`, `MAX_AIR_JUMPS`, `JUMP_SECONDARY_SCALE`.
- pacing: `GAP_BASE`, `GAP_RANGE`, `PAIR_GAP`.
- visuals: `SCALE`, `PENGUIN_SCALE`, `TILE_SCALE`.
- teams/icons: update `TEAMS` and `ICONS` maps.

