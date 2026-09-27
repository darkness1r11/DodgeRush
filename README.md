# Dodge Rush V4 — Boss Rush Edition

A portrait, offline-first Android arcade game built with native Kotlin + Canvas.

## What's new in V4
- **Fixed the broken GitHub Actions build.** The old workflow searched the repo
  for a file called `DodgeRush-V3-Source.zip` and tried to `unzip` it before
  building. If your repo contains the *extracted* project (folders, not a zip
  — which is what every other version of this project actually needs), that
  step always failed with "file not found." The new workflow builds straight
  from the checked-out repo — no zip-hunting, nothing to go wrong. See
  **How to build** below.
- **4th boss: REAPER.** Fires aimed volleys that track your lane instead of
  fixed spread patterns, and occasionally drops a homing mine (see below).
- **Boss enrage phase.** Every boss goes into an "ENRAGED" state at 35% HP:
  faster movement, faster fire rate, red warning flash. A visible last stretch
  instead of a flat fight.
- **New hazard: homing mine (red, pulsing, kind 5).** Slowly drifts toward
  your lane as it falls. Only appears during the REAPER fight — everywhere
  else the hazards are exactly as predictable as before.
- **New power-up: NOVA BOMB (white "N").** Instantly clears every obstacle and
  enemy bullet on screen, and if a boss is active, hits it for solid direct
  damage. A panic button for tight spots and a burst DPS tool during boss
  fights.

## Major features
- 7 ship skins with coin-priced unlocks
- Coin-based Hangar shop
- Four permanent upgrades: Blaster, Magnet, Shield, Chrono
- Five power-ups: Shield, Slow Time, Magnet, Overdrive, Nova Bomb
- Combo / near-miss bonus
- Endless difficulty and level progression
- Boss fights every ~45-52 seconds, four bosses in rotation:
  Sentinel, Vortex, Titan, Reaper — each with an enrage phase at low HP
- Boss health bars, projectile patterns, warning phase, rewards
- Five local, non-silent soundtrack loops:
  Neon Run, Pulse Reactor, Night Drive, Velocity, Boss Protocol
- Local SFX in resources
- No ads, analytics, accounts, backend, or INTERNET permission
- Android 8+ (API 26)
- All persistent progress is stored locally with SharedPreferences

## How to build (GitHub Actions, no computer needed)
1. Create (or reuse) a GitHub repo.
2. Extract this zip on your phone (any file manager / zip app can do this —
   you need the *folders*, not the zip itself, in the repo).
3. Upload the extracted contents to the repo root, so `settings.gradle.kts`
   and the `app/` folder sit directly at the top level of the repo (next to
   `.github/`). **Do not upload the .zip file itself** — that's the mistake
   the old workflow required and the new one refuses to build without a real
   project layout.
4. GitHub → Actions tab → "Build Dodge Rush APK" → Run workflow (or just push
   a commit; it runs automatically on `main`).
5. Wait for the green check.
6. Open the run → Artifacts → `DodgeRush-APK` → download, extract the zip,
   install `app-debug.apk`.
7. You'll need "install from unknown sources" allowed for whichever app you
   use to open the APK, since this isn't from the Play Store.
