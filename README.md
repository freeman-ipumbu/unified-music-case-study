# UNIFIED Music — Kotlin Multiplatform Case Study

![UNIFIED Music](assets/unified-music.svg)

**A local-first music system designed and engineered in Namibia—one coherent library, queue, player and audio-control experience.**

> This is a public product and engineering case study. Deployable source, device configuration, local media, build artefacts, credentials and private implementation details remain in a separate private repository.

## UNIFIED 3.0 — Namib After Dark

The 3.0 visual system moves away from generic neon glass toward a more ownable identity: obsidian night, warm dune light, Atlantic-blue information accents and restrained orchid highlights. Artwork remains the emotional centre while glass is limited to navigation and transient playback surfaces.

| Home | Now Playing |
| --- | --- |
| <img src="assets/unified-3-home.jpg" width="360" alt="UNIFIED 3.0 Home screen"> | <img src="assets/unified-3-now-playing.jpg" width="360" alt="UNIFIED 3.0 Now Playing screen"> |

These screens were captured from the installed `3.0-debug` build on a physical Android 15 device.

## UNIFIED 4.0 — Taste Memory

Version 4.0 turns the dormant recommendation foundation into a local-first listening intelligence system. It records credible starts, early skips and listened time on-device, restores that history across launches, and makes the result visible through a new Taste Memory dashboard plus Recently Played and Most Played shelves.

UNIFIED Mix now adapts from favourite, artist, album and recency signals. The system remains explainable and private: no listening history leaves the device, and provider integrations stay behind explicit capability boundaries.

## UNIFIED 5.0 — Seamless Queue

Version 5.0 moves the queue into Media3's native timeline. The complete playable queue is preloaded, track transitions are reflected back into shared product state, and shuffle plus repeat are owned by the playback service so system controls and the app stay coherent.

If playback advances while the interface is gone, relaunching reconnects to the engine's actual active track instead of stale persisted metadata. Removing an upcoming track rebuilds the native queue without losing the current song, position or play state.

<img src="assets/unified-5-home.png" width="420" alt="UNIFIED 5.0 running on a physical Android device with Taste Memory and the 3,795-track local library">

This is the installed `5.0-debug` build running against a 3,795-track on-device library on a physical Android 15 device.

## UNIFIED 6.0 — Library Vault

Version 6.0 fixes the collection-disappearance failure at the data boundary. The last healthy MediaStore index is encoded into a versioned snapshot and committed with Android atomic-file storage. Startup restores all 3,795 tracks before the platform scan completes; failed or transiently empty results keep that healthy snapshot visible instead of blanking the product.

MediaStore changes now trigger automatic reconciliation. A new Library Vault experience exposes secured, syncing and protected states, index freshness and on-device storage. The same release tightens the product's control hierarchy, segmented navigation, action cards, grouped rows, borders and radius language.

<img src="assets/unified-6-home.png" width="420" alt="UNIFIED 6.0 Library Vault showing 3,795 secured tracks on a physical Android device">

This cold-start capture is from the installed `6.0-debug` build. The device-side atomic snapshot was 870 KB and declared all 3,795 tracks after process restart.

## UNIFIED 7.0 — Collection DNA

Version 7.0 turns the durable collection into an explainable intelligence surface. Collection DNA calculates total playtime, format distribution, artwork coverage, lossless media, recent additions, metadata gaps and likely duplicates entirely on-device.

Six count-aware filters—All, Favorites, Downloaded, Lossless, Last 30 Days and Long Tracks—compose with sorting, Play All and Shuffle. Every reconciliation reports added, removed and refreshed items. Now Playing adds total remaining queue time and a functional sleep timer with four countdown presets plus stop-after-current-track behavior.

## UNIFIED 8.0 — Official Runnerz Music Player

![UNIFIED × Runnerz official music player ecosystem](assets/unified-runnerz-player.svg)

This is original ecosystem artwork for the 8.0 release. A current physical-device UI capture will replace or accompany it after the signed UNIFIED and Runnerz builds complete the documented handset round-trip gate; the device images above remain clearly versioned evidence from earlier releases.

Version 8.0 turns UNIFIED into the official music layer of the Runnerz ecosystem. The visual system now speaks the same language as the running product and its merch: **route lime** (`#39FF88`), **trail forest** (`#07120B`), **warm white** (`#F4FAF6`) and **founder gold** (`#D6B45A`). The result is one recognisable Namibian identity across listening, movement and the authored UNIFIED × Runnerz catalogue artwork.

### A music system built around how people move and listen

**Session Studio** creates five one-tap sessions from the listener's own library and on-device history: Daily Flow, Rediscover, Fresh Rotation, Deep Focus and Favorite Radio. Its results are stable for the same inputs and deliberately space repeat artists. **Track Radio** can expand any selected song into a ranked, taste-aware queue of up to 50 tracks using its artist, album, favourites and recent-listening signals. Neither system uploads listening history.

**Listening Universe** translates credible listening patterns into private progression rather than public engagement pressure. Nine persistent badges—including First Spark, Vault Keeper, Golden Ear, No-Skip Zone and Local Legend—show clear progress requirements and remain unlocked once earned. Five explainable archetypes—Pathfinder, Curator, Deep Diver, Sonic Purist and Artist Orbiter—reflect breadth, curation, listening depth, recording quality and artist focus. Levels and XP are calculated locally from plays, listening time, library depth, favourites and exploration.

### Runnerz sessions and handoff

Runnerz Mode builds private **30, 45, 60 or 90-minute** music arcs from the local collection. The selected tracks are artist-diversified and sequenced through warm-up, lock-in, tempo and finish-kick phases. Starting a session begins playback in UNIFIED, then hands only the session title, target duration and track count to an installed Runnerz production or field-test app; if neither package is available, Android falls back to the Runnerz website. Track identities and full listening history remain inside UNIFIED.

The sender and matching Runnerz receiver compile against the same explicit Android contract. A complete signed, physical-device start/run/return test remains a release gate, so this case study does not describe the cross-app link as production-complete yet.

### Rights-ready ShowTime Ambassador Channel

The **ShowTime Radio** surface is reserved for Shadrac “ShowTime” Mavungu as a Runnerz ambassador channel. It activates when local track metadata matches the declared ShowTime identity; a match does not establish approval or distribution rights. UNIFIED 8.0 does **not** bundle ambassador audio or artwork, copy protected media, promise a remote stream or imply distribution rights; editorial assets and distributable audio remain subject to explicit artist and rights-holder approval.

### Library Vault v2

The durable library now uses a checksummed, two-generation recovery design. Every new primary snapshot binds its header, timestamp, track count and body to an integrity checksum. Before replacement, the current valid snapshot is preserved as a separate atomic last-good generation. Startup validates the primary first and reads the last-good backup only when recovery is required; truncated or altered version 2 data is rejected, and version 1 snapshots remain readable for migration.

This release makes the ecosystem larger without weakening its boundary: local music, listening intelligence, achievements, run-session sequencing and Vault recovery remain on-device. Apple Music and Spotify production adapters still require registered applications, user authorisation and provider-approved infrastructure.

## My role

**Freeman Ipumbu — Product designer and software engineer**

I shaped the product direction, interaction and visual systems, shared domain model, Android playback runtime, provider-neutral catalog foundation and Kotlin Multiplatform architecture.

## The problem

Music collections become fragmented across devices, folders and services. Playback controls, queues, favourites, playlists and audio tuning often feel like separate tools rather than one understandable system.

UNIFIED explores a calmer local-first model:

```text
DISCOVER → ORGANISE → QUEUE → PLAY → SHAPE THE SOUND → RETURN
```

Local ownership and honest playback state come first. Streaming providers enter through explicit capability boundaries instead of compromising offline reliability or pretending protected provider audio can be treated like local media.

## Product response

- Android MediaStore discovery for large on-device libraries.
- Atomic Library Vault snapshots with instant restoration and empty-scan protection.
- Checksummed two-generation Vault recovery with legacy-snapshot compatibility.
- Automatic MediaStore change observation and background reconciliation.
- Collection DNA analysis, format distribution, artwork coverage, metadata-gap and duplicate-candidate reporting.
- Six live count-aware library filters that compose with sorting and playback.
- Media3/ExoPlayer foreground playback with a preloaded native queue, MediaSession, notification and lock-screen controls.
- Durable current-track, position, shuffle, repeat and exact queue-order restoration using stable media identities.
- Position-preserving queue editing, service-owned shuffle/repeat, native transition synchronisation, seeking and automatic completion handling.
- Remaining queue-time awareness and a countdown/end-of-track sleep timer.
- Persistent favourites and playlists with grouped artist and album views.
- Durable on-device Taste Memory with play, early-skip and listened-time signals.
- Explainable adaptive Smart Mix plus Recently Played and Most Played surfaces.
- Session Studio with five local, history-aware listening modes.
- Track Radio generated from a selected song and local taste signals.
- Listening Universe levels, XP, five archetypes and nine persistent unlockable badges.
- Duration-aware Runnerz music arcs with an explicit, minimal Android handoff.
- Rights-ready ShowTime Radio discovery for matching local tracks, with editorial and distribution use still approval-gated.
- Equaliser, bass, loudness and dynamics controls through Audio Lab.
- Audio-reactive spectrum and waveform visualisation.
- A Compose interface spanning Home, Library, Search, Playlists, Now Playing and Audio Lab.
- Provider-neutral Apple Music/Spotify gateway and ISRC-first cross-catalog merger; production adapters still require registered applications and credentials.

## Design approach

1. **Observe** — identify where local players fragment discovery, playback and organisation.
2. **Frame** — treat the queue and current track as one durable product state.
3. **Design** — build hierarchy around artwork, readable type, consistent controls and restrained motion.
4. **Connect the ecosystem** — use Runnerz colour, movement language and explicit app boundaries so the player feels native to the same product family.
5. **Localise the identity** — derive warmth and atmosphere from Namibia without reducing the interface to literal motifs.
6. **Build** — share domain and interface logic with Kotlin Multiplatform while keeping platform playback responsibilities explicit.
7. **Evaluate** — verify permissions, persistence, background playback and system media controls on physical hardware.
8. **Harden** — make automated tests, lint and reproducible builds release gates.

## Engineering overview

- Kotlin Multiplatform
- Jetpack Compose and Compose Multiplatform foundations
- Android MediaStore library discovery
- AndroidX Media3 / ExoPlayer playback service
- MediaSession, foreground notification and system transport controls
- Native equaliser, dynamics, bass and loudness processing
- Shared queue, playlist, provider, library and player domain models
- Preference-backed player, playlist, favourite, Audio Lab and listening-history state
- Android SDK 36 with minimum SDK 26
- GitHub Actions quality gate for tests, lint and debug APK assembly

## Verified evidence

- The complete UNIFIED 8.0 Android gate passed on 23 September 2026: 128 Gradle tasks covering shared logic and UI tests, app unit tests, lint and debug APK assembly.
- All 39 executed shared test cases passed with zero failures or errors.
- The shared test suite covers collection analysis, smart filters, reconciliation deltas, sleep timing, snapshot fidelity, empty-scan protection, queue preloading and background reconnection.
- Version 8.0 adds test coverage for Vault tamper recovery, five Session Studio modes, durable badge unlocks, Runnerz sequencing and handoff data, and ambassador metadata matching.
- Android lint completes with zero errors.
- Shared iOS simulator logic compiles successfully.
- Earlier versioned builds through 6.0 were installed and visually inspected on a physical HONOR Android 15 device; their captures are identified above.
- On that device, foreground/background playback, advancing position and system media metadata were verified through the active Media3 session.
- The 8.0 debug APK is built and checksummed, but has not yet been installed because the test handset is currently offline.

## Current boundary

Android is the production-focused implementation. The iOS target remains an early shell; native playback and shared production UI are not presented as complete.

Apple Music and Spotify production connections are not claimed. The provider-neutral gateway, capability model and catalog merger exist, but real adapters require registered applications, approved redirect URIs, signing identities and secure token infrastructure.

The UNIFIED-to-Runnerz sender and receiver are implemented and compile in their respective Android variants. Signed-build physical-device round-trip validation is still required before calling that handoff production-ready. ShowTime Radio is a metadata-matched local activation surface, not proof of media rights, a bundled catalogue or a streaming service.

## Next milestones

- Measured, configurable crossfade playback.
- Incremental library indexing and missing-file recovery.
- Feature-owned navigation and state modules.
- Signed physical-device validation of the complete UNIFIED → Runnerz → UNIFIED session loop.
- Consented run-state return without transferring full listening history between apps.
- Ambassador editorial and media publication only after explicit rights approval.
- Native iOS playback and remote-command integration.

## Repository boundary

The private repository contains the working implementation. This public case study intentionally excludes source code, local media, generated applications, device identifiers, environment files, credentials and internal recovery material.

---

© 2026 Freeman Ipumbu. Shared for portfolio evaluation; no licence is granted to reproduce the product or implementation.
