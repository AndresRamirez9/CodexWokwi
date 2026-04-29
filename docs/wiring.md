# Wiring and GPIO Mapping (Raspberry Pi Pico W)

## Components List (derived from provided `diagram.json`)

- 1x Raspberry Pi Pico / Pico W board
- 1x 4x4 membrane keypad
- 12x LEDs
  - 8x blue LEDs (labels 1..8)
  - 4x red LEDs (labels A..D)
- 12x 220Ω resistors (one per LED)
- 4x 1kΩ resistors (keypad row pull-up network)
- Shared ground wiring

## GPIO Assignment Table

### Keypad

| Keypad Signal | Pico W GPIO |
|---|---|
| C1 | GP19 |
| C2 | GP18 |
| C3 | GP17 |
| C4 | GP16 |
| R1 | GP26 |
| R2 | GP22 |
| R3 | GP21 |
| R4 | GP20 |

### LEDs

| Logical LED | Key | Pico W GPIO |
|---|---|---|
| LED1 | `1` | GP11 |
| LED2 | `2` | GP10 |
| LED3 | `3` | GP9 |
| LED4 | `4` | GP8 |
| LED5 | `5` | GP7 |
| LED6 | `6` | GP6 |
| LED7 | `7` | GP5 |
| LED8 | `8` | GP4 |
| LED9 | `A` | GP3 |
| LED10 | `B` | GP2 |
| LED11 | `C` | GP28 |
| LED12 | `D` | GP27 |

## Electrical Notes

- All LED cathodes connect to GND.
- Each LED anode is driven by a GPIO through a 220Ω series resistor.
- The diagram includes a resistor ladder tying keypad rows toward 3V3 through 1kΩ resistors.

## How to Run in Wokwi

1. Create a Pico-based simulation project.
2. Use provided keypad + LEDs wiring.
3. Place code from `src/main.cpp` into sketch file.
4. Start simulation and test keys:
   - `1..8` individual blue LEDs
   - `9` all blue ON, `0` all blue OFF
   - `A..D` individual red LEDs
   - `*` all red ON, `#` all red OFF

## How to Run on Real Hardware

1. Wire exactly as the GPIO tables above.
2. Verify resistor orientation/value:
   - LEDs: 220Ω
   - keypad network: 1kΩ
3. Upload firmware via Arduino-compatible RP2040 core.
4. Open serial monitor optionally (UART GP0/GP1 is present in diagram but not required by firmware).

## Assumptions

- The provided code is authoritative for GPIO-to-function mapping.
- Where diagram labels differ visually from logical LED indexing, firmware array order is treated as source of truth.
