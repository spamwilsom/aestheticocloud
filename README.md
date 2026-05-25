# The Sound & Light Room

**An adaptive light environment that translates crowd sound dynamics into luminous feedback — a living mirror of collective behavior.**

→ [Project Brief](https://aesthetico.cloud/sound-light-room/)    ·    [aesthetico.cloud](https://aesthetico.cloud)

-----

## Concept

This installation creates an immersive light environment that responds in real-time to the acoustic presence of people in a space. Distributed microphones translate crowd noise — conversations, laughter, shouts, silence — into visible patterns of light and darkness.

The twist: periodically and without announcement, the system inverts. Silence becomes luminous. Noise pulls the room toward dark. Strangers discover they can coordinate without speaking.

**The core question:** at what point does a group of individuals become a collective entity?

-----

## Status

`Concept & Research Phase` — Active development. Open to collaborators.

-----

## Repository Structure

```
sound-light-room/
├── README.md               ← you are here
├── index.html              ← project brief (web)
├── code/
│   ├── arduino/
│   │   └── sound_to_light/ ← Arduino sketch (mic → DMX/relay)
│   ├── pi/
│   │   └── main.py         ← Raspberry Pi version (Python)
│   └── web-demo/
│       └── index.html      ← browser demo (Web Audio API, no hardware needed)
└── docs/
    ├── system-diagram.md   ← signal flow: mic → controller → lights
    ├── wiring.md           ← hardware wiring reference
    └── calibration.md      ← mic placement and sensitivity tuning
```

> **Note:** `code/` and `docs/` are placeholders — this is where we build. See Contributing below.

-----

## Technical Stack

|Layer     |Component                                        |
|----------|-------------------------------------------------|
|Sensing   |Electret / condenser microphone array (2–10 mics)|
|Processing|Arduino Uno / Raspberry Pi + audio interface     |
|Control   |DMX controller → lighting fixtures               |
|Lighting  |LED PAR cans, floods, or panels on dimmer packs  |
|Power     |240V for stage lighting, 120V for control systems|
|Optional  |Pitch detection (FFT) → colour mapping           |

### Signal Flow

```
Microphones → Audio Interface → Microcontroller (Arduino/Pi)
           → DMX Controller → Lighting Fixtures
```

### The Inversion Logic

```
Normal mode:   loud crowd → brighter lights
Inversion:     loud crowd → darker lights   (triggered randomly)
```

Inversion timing is randomized to prevent predictability. Duration and frequency are calibrated parameters.

-----

## Versions

|Version        |Description                               |Budget (CAD) |
|---------------|------------------------------------------|-------------|
|**Minimal**    |Single zone, volume → brightness, 4–6 mics|~$1,500      |
|**Recommended**|Two zones, 6–10 mics, modular rig         |~$5,000–8,000|
|**Ideal**      |Multi-zone, pitch → colour, atmospheric   |~$15,000+    |

-----

## Getting Started (Hardware MVP)

### What you need

- 1× Arduino Uno or Raspberry Pi
- 1–4× electret condenser microphones
- 1× audio interface (if using Pi)
- 1× DMX USB interface
- LED lighting fixtures with DMX input (or relay-switched standard fixtures)
- DMX cable

### Quick wiring (Arduino)

1. Wire mic(s) to analog input pins (A0, A1, etc.)
1. Connect DMX shield or use SoftwareSerial on digital pins
1. Flash `code/arduino/sound_to_light/` sketch
1. Calibrate `THRESHOLD` and `INVERSION_INTERVAL` constants

### Browser demo (no hardware)

Open `code/web-demo/index.html` in Chrome/Firefox. Allow microphone access. The demo visualizes the volume-to-light logic using the Web Audio API — useful for understanding the mapping logic before touching hardware.

-----

## Contributing

This project is **CC0 — Public Domain**. Fork it, build it, adapt it to your space.

### Open roles

- Sound designer / audio engineer (mic calibration, spatial mapping)
- Programmer (sensor integration, real-time processing, DMX control)
- Electrician (code-compliant installation, power distribution)
- Lighting designer
- Fabricator / carpenter (temporary structures)
- Documentation (photo / video)

Pull requests welcome. If you’re building a version of this, open an issue and document it — we’d love to know where this ends up.

-----

## Influences

- James Turrell — atmospheric light environments, perceptual phenomena
- Olafur Eliasson — *Weather Project*, collective experience in constructed environments
- Participatory installation art
- Systems art and data visualization
- Sound-responsive environments

-----

## License

**CC0 1.0 Universal — Public Domain Dedication**

No rights reserved. Use freely, without attribution, for any purpose.

[Full license →](../LICENSE)

-----

*Part of [aesthetico.cloud](https://aesthetico.cloud) — a repository of aesthetically-driven concepts in progress.*