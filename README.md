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

<img src="keymap-drawer/roBa.svg" >
