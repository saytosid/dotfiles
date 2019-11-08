# Touchpad natural scrolling
```
xinput list # get device id
xinput list-props <device_id>
xinput --set-prop <device_id> "libinput Natural Scrolling Enabled" 1
```

# Touchpad driver - for scrolling etc
`xserver-xorg-input-libinput`

