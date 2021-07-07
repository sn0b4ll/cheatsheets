# Android Debug Bridge (adb)
#adb #port5555 

If port 5555 is open (or can be forwarded if you already have ssh access):
```
adb connect localhost:5555
adb shell
```

If 
`error: more than one device/emulator`
then
`adb devices`
`adb -s <specific device> shell`

Afterwards you can use `su root` to be root.
