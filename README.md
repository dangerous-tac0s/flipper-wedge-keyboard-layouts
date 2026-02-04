# Flipper Wedge Keyboard Layouts

Community keyboard layout files for the [Flipper Wedge](https://github.com/DangerousThings/flipper-wedge) app.

## What This Solves

The Flipper Wedge app types scanned UIDs via HID keyboard. By default, it sends US QWERTY keycodes, which produce wrong characters on non-US keyboard layouts. These layout files fix that.

**Example problem:** On a Hungarian keyboard, sending the US "0" keycode produces "ö" instead of "0".

## Installation

1. Download the layout file for your keyboard
2. Copy it to your Flipper Zero SD card at:
   ```
   /ext/apps_data/flipper_wedge/layouts/
   ```
3. Open Flipper Wedge → Settings → KB Layout
4. Select your layout from the list

## Available Layouts

### QWERTY Variants
| File | Language/Region | Notes |
|------|-----------------|-------|
| `us_qwerty.txt` | US English | Reference layout (same as built-in default) |
| `uk_qwerty.txt` | UK English | @ and " positions swapped |
| `spanish.txt` | Spanish | ñ key, inverted punctuation |
| `portuguese_br.txt` | Portuguese (Brazil) | ABNT2 layout |
| `portuguese_pt.txt` | Portuguese (Portugal) | Similar to Spanish |
| `italian.txt` | Italian | Standard Italian layout |
| `dutch.txt` | Dutch | Standard Dutch layout |
| `polish.txt` | Polish (Programmers) | Standard Polish layout |
| `turkish.txt` | Turkish Q | Turkish QWERTY variant |

### QWERTZ Variants
| File | Language/Region | Notes |
|------|-----------------|-------|
| `german.txt` | German | Z/Y swapped, umlauts |
| `swiss_german.txt` | Swiss German | Hybrid layout |
| `swiss_french.txt` | Swiss French | Hybrid layout |
| `hungarian.txt` | Hungarian | 0 is left of 1 |
| `czech.txt` | Czech | Numbers need SHIFT |

### AZERTY Variants
| File | Language/Region | Notes |
|------|-----------------|-------|
| `french.txt` | French | Numbers need SHIFT, A/Q and Z/W swapped |
| `belgian.txt` | Belgian | Similar to French AZERTY |

### Nordic Layouts
| File | Language/Region | Notes |
|------|-----------------|-------|
| `swedish.txt` | Swedish | å, ä, ö keys |
| `norwegian.txt` | Norwegian | æ, ø, å keys |
| `danish.txt` | Danish | æ, ø, å keys |
| `finnish.txt` | Finnish | Same as Swedish |

### Alternative Layouts
| File | Language/Region | Notes |
|------|-----------------|-------|
| `dvorak.txt` | Dvorak | Alternative ergonomic layout |
| `colemak.txt` | Colemak | Alternative ergonomic layout |

### Special
| File | Description |
|------|-------------|
| `numpad.txt` | Uses numpad keycodes (built-in, for reference) |
| `template.txt` | Template for creating your own layout |

## File Format

Layout files use Flipper's native format:

```
Filetype: Flipper Wedge Keyboard Layout
Version: 1
Name: My Layout

# Format: <character>: <hid_keycode> [SHIFT]
0: 39
1: 30 SHIFT
A: 4 SHIFT
a: 4
```

### HID Keycode Reference

**Number row (physical positions):**
```
Key:  `    1    2    3    4    5    6    7    8    9    0    -    =
Code: 53   30   31   32   33   34   35   36   37   38   39   45   46
```

**Letters:**
```
A=4  B=5  C=6  D=7  E=8  F=9  G=10 H=11 I=12 J=13 K=14 L=15 M=16
N=17 O=18 P=19 Q=20 R=21 S=22 T=23 U=24 V=25 W=26 X=27 Y=28 Z=29
```

**Modifiers:** Add `SHIFT` after the keycode if the character requires Shift.

Full reference: [USB HID Usage Tables](https://usb.org/sites/default/files/hut1_21.pdf) (page 83)

## Creating Your Own Layout

1. Copy `template.txt` to a new file
2. Test which physical key produces each character on your keyboard
3. Map characters to the corresponding HID keycodes
4. Only characters used in UID output need mapping: `0-9`, `A-F`, `a-f`, and delimiters

## Contributing

Found an error or want to add a layout? Pull requests welcome!

1. Test your layout on actual hardware
2. Include the language/region in the `Name:` field
3. Add comments explaining any quirks

## License

These layout files are provided under the MIT License. Use them freely.
