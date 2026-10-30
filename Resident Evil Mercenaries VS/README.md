# Resident Evil Mercenaries VS for PS Vita

Unofficial PS Vita port of the iOS version of **Resident Evil Mercenaries VS** (Capcom).

The port is a loader. It runs the game's own iOS ARM code natively on the Vita, with the iOS system parts (Objective-C runtime, Foundation, UIKit, OpenGL ES, audio) replaced by Vita code. **No game files are included.** You need your own copy of the iOS app (`.ipa`).

| | |
|---|---|
| Title ID | `REMV00001` |
| Version | 0.1 |
| Status | Tested and played on a real PS Vita and on Vita3K. |
| Download | [`remercvs.vpk`](remercvs.vpk) |

VPK SHA-256: `7ddd45f9ecb24cb3c92d47194214e1d71df1b48908c7ddbabb48029083ce2714`


## Requirements

- A PS Vita with HENkaku (Ensō or h-encore). A PS TV was not tested.
- **Enable unsafe homebrew** turned on in Settings > HENkaku Settings. The port is unsafe homebrew because it uses kubridge. VitaShell warns that it "requests extended permissions" when you install it.
- **kubridge** v0.3.1 or later by bythos14 ([releases](https://github.com/bythos14/kubridge/releases)):
  1. Copy `kubridge.skprx` to `ur0:tai/`.
  2. Under `*KERNEL` in `ur0:tai/config.txt`, add the line `ur0:tai/kubridge.skprx`. If you have `ux0:tai/config.txt`, taiHEN uses that file instead, so add the line there.
  3. Reboot.
- **libshacccg.suprx** (Sony's shader compiler) in `ur0:data/` or `ur0:data/external/`. Extract it with [ShaRKBR33D](https://github.com/Rinnegatamante/ShaRKBR33D) or ShaRKF00D.
- Your own **iOS `.ipa`** of the game, version 1.10.10 (decrypted).
- About 70 MB free on `ux0:` for the unpacked game.

## The IPA

| | |
|---|---|
| Bundle | `jp.co.capcom.biovsus` (`BioVS_en.app`, shown as "RE VS.") |
| Version | 1.10.10 (minimum iOS 4.2) |
| Size | 30,182,475 bytes |
| MD5 | `12ebe138bc7759f8a446bf551d3f40fb` |
| SHA-1 | `2eed0039d1f6006027e42b495dfc4c56ed3842fa` |
| SHA-256 | `271fb9523dfbdcbb648314ee0b400b7fb26a603c41f6be03da6206a0f6c4c4b0` |

The port uses the game code at fixed addresses, so only version 1.10.10 works. Another copy of 1.10.10 can have a different whole-file hash and still work. What must match is the executable inside it:

| File inside the IPA | Size | SHA-256 |
|---|---|---|
| `Payload/BioVS_en.app/BioVS_en` | 6,593,872 bytes | `a9ca1e19c5f4479dec3935a0e2ef269a7603e794eb3c0ebb26f9a57530f52407` |

It must be decrypted. The port checks its `LC_UUID` (`0d74ac58-8f9d-8981-b5a3-36ea5ec6e8aa`) and stops with a message if it is a different build.

## Installation

1. In Settings > HENkaku Settings, turn on **Enable unsafe homebrew**.
2. Install kubridge and libshacccg.suprx (see Requirements) and reboot.
3. Install `remercvs.vpk` with VitaShell.
4. Create the folder `ux0:data/remercenariesvs/`.
5. Copy your `.ipa` into that folder. Any file name that ends in `.ipa` works, for example:

   ```
   ux0:data/remercenariesvs/Resident Evil Mercenaries VS.ipa
   ```

6. Start **RE Mercenaries VS** from the LiveArea.

## Known issues and limitations

- Online and local (Bluetooth) multiplayer do not work. Single Player (Training, Coin Shoot) works.


## Troubleshooting

For any problem, open an issue and attach `ux0:data/remercenariesvs/log.txt`.

## Credits

- **Capcom**: Resident Evil Mercenaries VS.
- **Rinnegatamante**: vitaGL, vitaShaRK and ShaRKBR33D.
- **bythos14**: kubridge.
- **Sean Barrett**: stb_image.
- **David Reid**: dr_mp3 and dr_wav.
- **The VitaSDK team.**

## Legal

This project is not affiliated with or endorsed by Capcom. No game code or data is included or distributed. Use a copy of the game that you own.
