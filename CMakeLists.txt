cmake_minimum_required(VERSION 3.13)
project(pico_w_keypad_leds C CXX ASM)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

# NOTE:
# This repository keeps the original Arduino-style sketch logic unchanged in src/main.cpp.
# Build this project using an Arduino-compatible RP2040 environment (e.g. Arduino IDE, PlatformIO,
# or Wokwi Arduino simulation profile with the Keypad library available).

add_custom_target(info ALL
  COMMAND ${CMAKE_COMMAND} -E echo "Use an Arduino RP2040 toolchain to compile src/main.cpp"
)
