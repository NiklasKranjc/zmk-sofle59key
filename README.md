# Sofle Choc 1 Encoder
*my shop https://keyboard-hoarders.com & https://keyboardhoarders.etsy.com*

![59key](https://github.com/user-attachments/assets/d4e1a4c2-87b7-4b6a-aeb6-3dece8e13aaf)


## Keymap


![sofle59keyEncRight](https://github.com/user-attachments/assets/dff333a7-ba96-4db6-8968-be696cdbb430)

## How bluetooth profiles work


![soflebluetooth](https://github.com/user-attachments/assets/48da49ea-8202-4d37-804f-d13929569938)

## Troubleshooting

### Bluetooth not working after enabling mouse keys (CONFIG_ZMK_POINTING)

When you enable mouse/pointing features (`CONFIG_ZMK_POINTING=y` in `sofle.conf`), the keyboard's HID descriptor changes. Your computer may cache the old descriptor, causing Bluetooth connectivity issues.

**Solution:**

1. **On your computer/device:** Go to Bluetooth settings and "Forget" or remove the keyboard
2. **On the keyboard:** Clear Bluetooth bonds by pressing the `BT_CLR_ALL` key combination (accessible in the ADJUST layer by holding both LOWER and RAISE simultaneously)
3. **Re-pair:** Put the keyboard back in pairing mode and pair it fresh with your device

This is expected behavior with ZMK when changing HID features. After re-pairing, both keyboard and mouse keys should work over Bluetooth.

### Mouse keys working over USB but not Bluetooth

Some controllers (especially Seeeduino XIAO BLE) have known issues with mouse keys over Bluetooth. The nice!nano controllers (used in this build) generally work well.

If you still have issues:
- Make sure you've flashed both halves of the split keyboard
- Try using USB logging to check for errors
- Update to the latest ZMK firmware (rebuild via GitHub Actions)
