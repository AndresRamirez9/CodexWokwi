# Architecture

## 1. Firmware Style

The firmware is a single-file Arduino-style application in `src/main.cpp` with two lifecycle functions:

- `setup()`: initializes all LED GPIO pins as outputs and sets initial LOW state.
- `loop()`: scans keypad events and applies LED state changes according to key pressed.

## 2. Data Model in Code

- `keys[4][4]`: keypad symbol matrix layout.
- `ledPins[12]`: GPIO map for 12 LEDs.
- `rowPins[4]`: GPIO map for keypad row lines.
- `colPins[4]`: GPIO map for keypad column lines.

The `Keypad` object ties these arrays into the key scanning driver.

## 3. Control Logic

On each loop iteration:
1. Read one key with `keypad.getKey()`.
2. If key is valid (`!= NO_KEY`), run a `switch` dispatch.
3. Set one or multiple LEDs HIGH/LOW based on command key.
4. Delay 10 ms for scan pacing.

## 4. Behavioral Guarantees

- The original key-to-action mapping is unchanged.
- LED states are latch-style (persist until another key changes them).
- Numeric LED bank (`1..8`) and alpha LED bank (`A..D`) can be controlled independently.

## 5. Assumptions and Compatibility

- Source code depends on Arduino core APIs and the `Keypad` library.
- GPIO numbering is Broadcom-style GP pin numbers as used by RP2040 Arduino cores.
- External pull-up network present on keypad rows (per provided diagram) is preserved in documentation.
