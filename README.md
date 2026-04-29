# Raspberry Pi Pico W Keypad-to-LED Controller

This repository contains a **documentation-first, cleaned project layout** for a Raspberry Pi Pico W project where a **4x4 keypad** controls **12 LEDs**.

> Core firmware behavior is preserved from the provided source code (`setup()` / `loop()` with `Keypad` library).

## Repository Structure

```text
.
├── CMakeLists.txt
├── diagram.json
├── include/
├── src/
│   └── main.cpp
└── docs/
    ├── architecture.md
    └── wiring.md
```

## Project Overview

- Platform target: Raspberry Pi Pico W (RP2040)
- Firmware style: Arduino-compatible C++ sketch logic
- Input: 4x4 matrix membrane keypad
- Output: 12 discrete LEDs (8 blue for numeric zone, 4 red for A-D zone)

## Features

- Keypad numeric keys `1..8` turn on corresponding blue LEDs.
- Key `9` turns on all first 8 LEDs.
- Key `0` turns off all first 8 LEDs.
- Keys `A..D` turn on their corresponding red LEDs.
- Key `*` turns on all 4 red LEDs.
- Key `#` turns off all 4 red LEDs.

## Build / Flash Options

Because the code uses Arduino API (`pinMode`, `digitalWrite`, `delay`) and `Keypad.h`, use an **Arduino-compatible RP2040 environment**.

### Option A: Wokwi (recommended for quick simulation)
1. Create/import a Raspberry Pi Pico project in Wokwi.
2. Copy `src/main.cpp` logic into `sketch.ino`.
3. Use the provided `diagram.json` wiring (or replicate from `docs/wiring.md`).
4. Ensure `Keypad` library is enabled in the simulation environment.
5. Start simulation and press keypad buttons.

### Option B: Real Raspberry Pi Pico W (Arduino IDE)
1. Install Arduino IDE.
2. Install RP2040 board package (e.g., "Raspberry Pi Pico/RP2040").
3. Install the `Keypad` library via Library Manager.
4. Create a sketch and paste `src/main.cpp` logic.
5. Select board: **Raspberry Pi Pico W** and correct USB port.
6. Upload and test with hardware wired as documented in `docs/wiring.md`.

## Notes on Pico SDK

A minimal `CMakeLists.txt` is included only to provide a standard repo skeleton. The supplied code is Arduino-oriented and is not rewritten to native Pico SDK APIs to avoid logic/behavior changes.

## Wi-Fi and Secrets

This firmware does **not** use Wi-Fi or credentials. No secret material is required.

## Documentation Index

- Architecture: [`docs/architecture.md`](docs/architecture.md)
- Wiring & GPIO map: [`docs/wiring.md`](docs/wiring.md)
