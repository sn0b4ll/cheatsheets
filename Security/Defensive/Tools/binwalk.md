# Binwalk
https://github.com/ReFirmLabs/binwalk

- Find files in other files
- Get sections in firmware images etc.

```
➜  binwalk <example>.jpg 

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             JPEG image data, JFIF standard 1.01
97465         0x17CB9         Zip archive data, at least v2.0 to extract, name: donotshare
99087         0x1830F         Zip archive data, at least v1.0 to extract, name: __MACOSX/
99142         0x18346         Zip archive data, at least v2.0 to extract, name: __MACOSX/._donotshare
99574         0x184F6         End of Zip archive, footer length: 22
```