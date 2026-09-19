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
- Media3/ExoPlayer foreground playback with MediaSession, notification and lock-screen controls.
- Durable current-track, position, shuffle, repeat and exact queue-order restoration using stable media identities.
- Queue editing, shuffle, repeat, seeking and automatic completion handling.
- Persistent favourites and playlists with grouped artist and album views.
- Explainable Smart Mix and listening-intelligence foundations.
- Equaliser, bass, loudness and dynamics controls through Audio Lab.
- Audio-reactive spectrum and waveform visualisation.
- A Compose interface spanning Home, Library, Search, Playlists, Now Playing and Audio Lab.
- Provider-neutral Apple Music/Spotify gateway and ISRC-first cross-catalog merger; production adapters still require registered applications and credentials.

## Design approach

1. **Observe** — identify where local players fragment discovery, playback and organisation.
2. **Frame** — treat the queue and current track as one durable product state.
3. **Design** — build hierarchy around artwork, readable type, consistent controls and restrained motion.
4. **Localise the identity** — derive warmth and atmosphere from Namibia without reducing the interface to literal motifs.
5. **Build** — share domain and interface logic with Kotlin Multiplatform while keeping platform playback responsibilities explicit.
6. **Evaluate** — verify permissions, persistence, background playback and system media controls on physical hardware.
7. **Harden** — make automated tests, lint and reproducible builds release gates.

## Engineering overview

- Kotlin Multiplatform
- Jetpack Compose and Compose Multiplatform foundations
- Android MediaStore library discovery
- AndroidX Media3 / ExoPlayer playback service
- MediaSession, foreground notification and system transport controls
- Native equaliser, dynamics, bass and loudness processing
- Shared queue, playlist, provider, library and player domain models
- Preference-backed player, playlist, favourite and Audio Lab state
- Android SDK 36 with minimum SDK 26
- GitHub Actions quality gate for tests, lint and debug APK assembly

## Verified evidence

- Clean Android build matrix completed successfully.
- Eleven shared Android tests pass with zero failures.
- Android lint completes with zero errors.
- Shared iOS simulator logic compiles successfully.
- Installed and visually inspected on a physical HONOR Android 15 device.
- Foreground and background playback verified through the active Media3 session.
- Playback position continued advancing after the app moved to the background.
- System media metadata reported the correct track, artist and album.

## Current boundary

Android is the production-focused implementation. The iOS target remains an early shell; native playback and shared production UI are not presented as complete.

Apple Music and Spotify production connections are not claimed. The provider-neutral gateway, capability model and catalog merger exist, but real adapters require registered applications, approved redirect URIs, signing identities and secure token infrastructure.

## Next milestones

- Measured gapless and crossfade playback.
- Incremental library indexing and durable listening history.
- Feature-owned navigation and state modules.
- Native iOS playback and remote-command integration.

## Repository boundary

The private repository contains the working implementation. This public case study intentionally excludes source code, local media, generated applications, device identifiers, environment files, credentials and internal recovery material.

---

© 2026 Freeman Ipumbu. Shared for portfolio evaluation; no licence is granted to reproduce the product or implementation.
