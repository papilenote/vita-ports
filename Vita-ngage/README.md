# Vita-ngage for PS Vita

Unofficial PS Vita launcher for **N-Gage** games (Nokia).


| | |
|---|---|
| Title ID | `NGAG00001` |
| Version | 0.2 |
| Status | Tested and played on a real PS Vita and on Vita3K. |
| Download | [`vitangage.vpk`](vitangage.vpk) |

VPK SHA-256: `2f5e79ab042908cc68dce2e4e20b23e38f8e3258b0b7cde142edc9ea530d7cc7`


## Requirements

- A PS Vita or PS TV with HENkaku (Ensō, h-encore or HENlo).
- **Enable unsafe homebrew** turned on in Settings > HENkaku Settings. The port is unsafe homebrew because it uses kubridge. VitaShell warns that it "requests extended permissions" when you install it.
- **kubridge** v0.3.1 or later by bythos14 ([releases](https://github.com/bythos14/kubridge/releases)):
  1. Copy `kubridge.skprx` to `ur0:tai/`.
  2. Under `*KERNEL` in `ur0:tai/config.txt`, add the line `ur0:tai/kubridge.skprx`. If you have `ux0:tai/config.txt`, taiHEN uses that file instead, so add the line there.
  3. Reboot.
- **libshacccg.suprx** (Sony's shader compiler) in `ur0:data/` or `ur0:data/external/`. Extract it with [ShaRKBR33D](https://github.com/Rinnegatamante/ShaRKBR33D) or ShaRKF00D.
- Your own **`.n-gage` packages** of the games (see the compatibility list).

## Compatibility

| Game | Engine | Status |
|---|---|---|
| Crash Bandicoot Nitro Kart 3D | Symbian (native) | Full game |
| Metal Gear Solid Mobile | Airplay (s3e) | Full game |
| Mile High Pinball | Airplay (s3e) | Full game |
| Resident Evil Degeneration | Airplay (s3e) | Full game |
| System Rush: Evolution | Airplay (s3e) | Full game |
| Tomb Raider: Underworld | Symbian (native) | Trial only |

The launcher lists a game only when its package is in `ux0:data/vitangage/`. It finds each package by its CRC-32, so only these packages are listed:

| Game | Package size | CRC-32 | MD5 | SHA-1 | SHA-256 |
|---|---|---|---|---|---|
| Crash Bandicoot Nitro Kart 3D | 5,906,195 bytes | `1ED873EB` | `25eeb17ce77cf2c618386573907bc394` | `033dbdbe712b5134d70a7cd58602d5219708c8c6` | `92495ba3efdcd16894d79837fe3c533ca581b1d0abbcb419eeb65e02990db62e` |
| Metal Gear Solid Mobile | 2,542,447 bytes | `0EDFEEDE` | `e7aa373d96c3f80b3b677c29ff91efda` | `e373f2a1dabbbd473ac232c13c309bb8f145e3d4` | `575afba9a431775edd30e20a54e23380d182560d7d51db90ae5edd5b810b2d81` |
| Mile High Pinball | 14,912,063 bytes | `88D5F1A9` | `a788c1c11dc94d816cce27fe1c67f9b5` | `098326ac17491e7c514840189a2f87154476e577` | `4f33f5ca50ec70e25c12075f9222b4805f3d43cb3ae4a7963334722a569072f9` |
| Resident Evil Degeneration | 2,435,823 bytes | `35B5BB54` | `047fec61a321d169593536a4556b59c5` | `acb144f5b4432d49f1b8f940a69330fc7f7f7390` | `8f086162778b323c25aee89a4b582708ab3bee87f62cf30c29fa723da1a9998c` |
| System Rush: Evolution | 12,803,901 bytes | `8A76A3BB` | `7f4adbd46367587838f5c60bd08d1b96` | `cb1b02f8ecad866d0174298258b2d571c7fb8c6f` | `263014ee304ba75ce8bdc812cfcb7f2e502d4d58cfb6e94374ebc2a82a8c9859` |
| Tomb Raider: Underworld | 2,039,701 bytes | `5077A9CA` | `afc760d721d1b430680f52e740170dd3` | `fa350e276d6945f90c04f8592c3603e83ee24499` | `2a54beee46d3408962c78c7fcb54d54ceddafbebd6d95f518d6db495da7ea468` |

### Patches

| Name | 60 FPS | Widescreen | Vita icons | Full game |
|---|:---:|:---:|:---:|:---:|
| Crash Bandicoot Nitro Kart 3D | ❌ | ❌ | ❌ | ✅ |
| Metal Gear Solid Mobile | ✅ | ✅ | ✅ | ✅ |
| Mile High Pinball | ❌ | ❌ | ❌ | ✅ |
| Resident Evil Degeneration | ✅ | ✅ | ✅ | ✅ |
| System Rush: Evolution | ❌ | ✅ | ❌ | ✅ |
| Tomb Raider: Underworld | ❌ | ❌ | ❌ | ❌ |


## Installation

1. In Settings > HENkaku Settings, turn on **Enable unsafe homebrew**.
2. Install kubridge and libshacccg.suprx (see Requirements) and reboot.
3. Install `vitangage.vpk` with VitaShell.
4. Create the folder `ux0:data/vitangage/`.
5. Copy your `.n-gage` packages into that folder. Any file names work, for example:

   ```
   ux0:data/vitangage/Metal.Gear.Solid.Mobile.n-gage
   ux0:data/vitangage/Resident.Evil.Degeneration.n-gage
   ```

6. Start **Vita-ngage** from the LiveArea and pick a game with left / right. The first start of a game installs it from its package into its own folder, `ux0:data/vitangage/<game>/`.

In a game, **Start + Select** goes back to the launcher. The launcher remembers the last game.


## Troubleshooting

For any problem, open an issue and attach the logs: `ux0:data/vitangage/log.txt` (the launcher) and `ux0:data/vitangage/<game>/log.txt` (the game).

## Credits

- **Nokia**: N-Gage 2.0.
- **Rinnegatamante**: vitaGL, vitaShaRK and ShaRKBR33D.
- **bythos14**: kubridge.
- **Igor Pavlov**: the LZMA SDK.
- **Sean Barrett**: stb_image.
- **David Reid**: dr_mp3 and dr_wav.
- **The DejaVu fonts** authors.
- **The VitaSDK team.**

## Legal

This project is not affiliated with or endorsed by Nokia or the games' publishers. No game code or data is included or distributed. Use packages of games that you own.