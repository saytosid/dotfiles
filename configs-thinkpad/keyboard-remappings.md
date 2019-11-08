# Keyboard remappings for X1C2
#### Taken from: https://wiki.archlinux.org/index.php/Lenovo_ThinkPad_X1_Carbon_(Gen_2)#Remapping_keys_using_xmodmap
#### and https://superuser.com/questions/760602/how-to-remap-keys-under-linux-for-a-specific-keyboard-only/1398289

# Changes
- backspace and delete be 'BackSpace', while functioning as 'Delete' when you hold down shift
- Exc-> Tilde/backspace
- Home/End -> Esc

- Get the kb device id - AT Translated Set 2 keyboard 
`xinput list`

- Get keymappings for this kd
`setxkbmap -device <device_id> -print`

- Create a file - /usr/share/X11/xkb/symbols/custom
```
xkb_symbols "remote" {
    key <ESC>  { [ grave, asciitilde ] };
    key <HOME> { [ Escape ] };
    key  <END> { [ Escape ] };
    key <BKSP> { [ BackSpace, Delete ] };
    key <DELE> { [ BackSpace, Delete ] };
};
```

- `setxkbmap -device <device id> -print | grep xkb_symbols` and add `+custom`

- `setxkbmap -device <device id> -layout "pc+us+inet(evdev)+custom"`

- Add to ~/.profile (10==<device_id>)
`setxkbmap -device 10  -layout "pc+us+inet(evdev)+custom"`
