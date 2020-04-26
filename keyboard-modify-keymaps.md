# Change keyboard layout / remap keys

* Find out a keycode using `xev`
* To remap keys, use `xmodmap`, e.g. `xmodmap -e "keycode 104 = braceright"`
* To make this permanent: `xmodmap -pke >~/.Xmodmap`

## Example

This gives you easier access to backslash and left and right braces using numpad keys:

```
xmodmap -e "keycode 90 = backslash"
xmodmap -e "keycode 86 = braceleft"
xmodmap -e "keycode 104 = braceright"
xmodmap -pke >~/.Xmodmap
```
