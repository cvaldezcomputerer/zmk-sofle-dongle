# ZMK Sofle Wireless Dongle Keyboard

This is a ZMK firmware configuration for a Sofle split keyboard with a wireless dongle setup.

## Features

- **Split keyboard**: Sofle layout (two keyboard halves + central dongle)
- **Wireless**: Uses nice!nano v2 controllers with Bluetooth
- **Dongle with display**: The central dongle has an OLED display (SH1106, 128x64)
- **Nice!View displays**: The left and right keyboard halves also have displays
- **ZMK Studio support**: For live remapping
- **RGB & encoders**: Supports rotary encoders and RGB lighting
- **Low power consumption**: Optimized sleep modes

## Display Customization

The dongle display images are defined in an external ZMK module called [zmk-dongle-display](https://github.com/englmaxi/zmk-dongle-display) (by englmaxi, v0.3).

To customize the display images:
1. Fork or modify the [zmk-dongle-display](https://github.com/englmaxi/zmk-dongle-display) repository
2. Look for image/widget files (likely `.c` files with pixel/bitmap data)
3. Update `config/west.yml` to point to your fork

Display configuration options are controlled in `config/eyelash_sofle.conf`, including battery display and macOS modifier icons.

## Keymap Structure

The keyboard uses a 65-key layout with the following components:

### Hardware Features
- **Rotary encoder** (top-left): Volume control on Layer 0, scroll on Layer 1
- **Directional joystick** (center column): Four-way directional control (up/down/left/right arrows on Layer 0, mouse movement on Layer 1+)
- **Center button press**: Enter/Return key

### Layer 0 (Base Layer)
Standard QWERTY layout with some customizations:
- **Row 1**: ESC, numbers 1-0, MINUS
- **Row 2**: CAPS, QWERTY top row, EQUAL
- **Row 3**: TAB, QWERTY home row, APOS
- **Row 4**: LSHIFT, QWERTY bottom row, BACKSLASH
- **Thumb cluster**:
  - Left: CTRL, Tab+Shift+Ctrl (hold layer 3), GUI, SPACE, Layer 1 (momentary)
  - Right: SPACE, BACKSPACE, Tab+Ctrl (hold layer 2), { (LBRC), } (RBRC)

**Special keys:**
- `lt 3 LS(LC(TAB))`: Tap for Shift+Ctrl+Tab (previous tab), hold for Layer 3
- `lt 2 LC(TAB)`: Tap for Ctrl+Tab (next tab), hold for Layer 2
- `mo 1`: Hold for Layer 1 (momentary activation)

### Layer 1 (Function & Numbers)
- **Row 1**: Function keys F1-F10, backtick on far left
- **Row 2**: GRAVE, numbers 2-3, Shift+GUI+4 (screenshot), then PgUp/End/Up/Home on right
- **Row 3**: Numbers 1-9, 0 across the home row
- **Row 4**: RGB controls on left, F11/F12/INSERT on right
- Center joystick controls mouse movement in this layer

### Layer 2 & 3
- Bluetooth controls, system functions, and additional utilities

## Troubleshooting

- If the halves do not pair after `settings_reset`, keep the dongle and both halves powered at the same time while flashing the reset firmware and the normal firmware. Powering everything together helps the automatic pairing complete.

---


