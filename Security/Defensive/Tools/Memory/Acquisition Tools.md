# Windows

# Linux
## Image
- LiME ([Github](https://github.com/504ensicsLabs/LiME))
- Pmem from Rekall 
  - linpmem - might dump 33TB of virtual address memory --> rekal aff4acquire
- LMAP from Rekall

### Possible way
rekal --> aff4akquire then

`rekal aff4export <path_to_aff4> --dump-dir=<output_dir>`
TODO Document more detailed


## Profile
- Dwarfdump + convert.py from vol ([Details](https://code.google.com/archive/p/volatility/wikis/LinuxMemoryForensics.wiki))

# Mac
- Mac Memory Reader (Website no longer active, not working with current versions)
- Mac Memoryze (10.6 to 10.8, [Fireeye](https://fireeye.market/apps/211372))
- OSXPmem (way to go, was moved from rekall to aff4 [Github](https://github.com/Velocidex/c-aff4/tree/master/tools/pmem))