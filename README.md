# UNIFIED Music — Kotlin Multiplatform Case Study

![UNIFIED Music](assets/unified-music.svg)

**A local-first music experience exploring one coherent library, player, queue and audio-control system across mobile platforms.**

> This is a public product and engineering case study. Deployable application source, device configuration, local media, build artefacts and private implementation details remain in a separate private repository.

## My role

**Freeman Ipumbu — Product designer and software engineer**

I shaped the product direction, interaction system, visual language, shared domain model, Android playback implementation and Kotlin Multiplatform architecture.

## The problem

Music collections become fragmented across devices, folders and services. Playback controls, queues, favourites, playlists and audio tuning often feel like separate tools rather than one understandable system.

UNIFIED explores a calmer local-first model:

```text
DISCOVER → ORGANISE → QUEUE → PLAY → SHAPE THE SOUND → RETURN
```

The product prioritises direct ownership of local music, visible playback state and a consistent interface without pretending unfinished cross-platform or network features already exist.

## Product response

- Local Android music discovery through the platform media library.
- Queue, shuffle, repeat, seek and restored playback position.
- Favourites, library sorting and grouped artist and album views.
- Playlist creation, track actions and queue-editing foundations.
- Smart-queue and listening-intelligence domain models.
- Real-time equaliser, bass, loudness and dynamics controls.
- Audio-reactive spectrum and waveform visualisation foundations.
- A Compose interface spanning Home, Library, Playlists and Audio Lab.
- Clear separation between shared music logic, shared UI and platform audio code.

## Design approach

1. **Observe** — identify where local music players fragment discovery, playback and organisation.
2. **Frame** — treat the queue and current track as one durable product state.
3. **Design** — build a visual system around artwork, readable hierarchy and restrained motion.
4. **Build** — share domain and interface logic with Kotlin Multiplatform while keeping platform audio responsibilities explicit.
5. **Evaluate** — verify library, playback, persistence and device-permission behaviour before expanding the platform surface.
6. **Harden** — add meaningful tests, background media indexing and honest failure states before release claims.

## Engineering overview

- Kotlin Multiplatform
- Jetpack Compose and Compose Multiplatform foundations
- Android MediaStore library discovery
- Android `MediaPlayer` playback and audio focus
- Native equaliser, dynamics, bass and loudness processing
- Shared queue, playlist, library and player domain models
- Local preference-backed playback and favourite state
- Android SDK 36 with minimum SDK 26

## Current status

The Android implementation is a substantial working prototype, not a public release. A debug build has been produced from the current source generation, while a fresh clean build still needs to be repeated against a restored Android SDK toolchain.

Playlist persistence is implemented in the domain layer but not yet connected to the active interface. Audio profiles, listening history and smart-mix behaviour need full persistence and integration. Automated tests are currently foundational rather than release-grade.

The iOS target remains an early shell; shared production UI and native iOS playback are not presented as complete.

## Product boundary

UNIFIED currently focuses on music stored on the device. It does not claim streaming-service integration, mesh synchronisation, cross-device playback or production-ready iOS support.

## Repository boundary

The private source repository contains the working implementation. This public case study intentionally excludes source code, local media, generated applications, device identifiers, environment files, credentials and internal recovery material.

---

© 2026 Freeman Ipumbu. Shared for portfolio evaluation; no licence is granted to reproduce the product or implementation.
