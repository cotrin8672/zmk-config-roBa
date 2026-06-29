# zmk-config-roBa

This fork targets XIAO nRF52840 Plus for temporary hand-wired bring-up.

The ZMK build still uses the upstream `seeeduino_xiao_ble` board because the
MCU and bootloader target are compatible. The extra Plus pads are referenced by
their nRF52840 GPIO names:

- D11 / P0.15 replaces the original NFC2 / P0.10 pad.
- P1.01 replaces the original NFC1 / P0.09 pad. The first Plus mapping used
  P0.19, but P1.01 is used now so a damaged P0.19 pad is not required.

`CONFIG_NFCT_PINS_AS_GPIOS` is not needed because this mapping no longer uses
the NFC pins.

For a temporary trackball-only bring-up without back-side Plus pads, flash
`roBa_R_trackball_test_side_pins`. This test firmware moves PMW3610 CS to the
normal side pin D10 and only keeps a minimal matrix pin alive for build
compatibility:

- D5 / P0.05 -> PMW3610 SCLK
- D4 / P0.04 -> PMW3610 SDIO
- D10 / P1.15 -> PMW3610 NCS / CS
- D0 / P0.02 -> PMW3610 MOTION
- 3V3 -> PMW3610 VCC / Vin
- GND -> PMW3610 GND

<img src="keymap-drawer/roBa.svg" >
