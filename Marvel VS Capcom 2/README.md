# Marvel vs. Capcom 2 for PS Vita

Unofficial PS Vita port of the iOS version of **Marvel vs. Capcom 2: New Age of Heroes** (Capcom, 2012).

The port is a loader. It runs the game's own iOS ARM code natively on the Vita, with the iOS system parts (Objective-C runtime, Foundation, UIKit, OpenGL ES, OpenAL, threads) replaced by Vita code. **No game files are included.** You need your own copy of the iOS app (`.ipa`).

| | |
|---|---|
| Title ID | `MVSC00001` |
| Version | 1.0 |
| Status | Tested on a real PS Vita and in Vita3K |
| Download | [`mvc2.vpk`](mvc2.vpk) |

VPK SHA-256: `820849a75d0889adfd48e2d0302b70e8669b83bd22dd785bdde20645e1ca03d4`

## Requirements

- A PS Vita with HENkaku (Ensō or h-encore). A PS TV was not tested.
- **Enable unsafe homebrew** turned on in Settings > HENkaku Settings. The port is unsafe homebrew because it uses kubridge. VitaShell warns that it "requests extended permissions" when you install it.
- **kubridge** v0.3.1 or later by bythos14 ([releases](https://github.com/bythos14/kubridge/releases)):
  1. Copy `kubridge.skprx` to `ur0:tai/`.
  2. Under `*KERNEL` in `ur0:tai/config.txt`, add the line `ur0:tai/kubridge.skprx`. If you have `ux0:tai/config.txt`, taiHEN uses that file instead, so add the line there.
  3. Reboot.
- **libshacccg.suprx** (Sony's shader compiler) in `ur0:data/` or `ur0:data/external/`. Extract it with [ShaRKBR33D](https://github.com/Rinnegatamante/ShaRKBR33D) or ShaRKF00D.
- Your own **iOS `.ipa`** of the game, version 1.00.00 (decrypted).
- About 330 MB free on `ux0:` for the first start (the `.ipa` and the unpacked game). After the first start the `.ipa` can be deleted; the unpacked game takes 167 MB.

## The IPA

| | |
|---|---|
| Bundle | `jp.co.capcom.marvelcap2us` (`MarvelCap2Us.app`, shown as "MVC2") |
| Version | 1.00.00 (minimum iOS 5.0) |
| Size | 152,466,014 bytes |
| MD5 | `7c496a0f0f565d962b7580d82f4cfbe2` |
| SHA-1 | `4953c2dfd5a3e320cbd5c4dae48b1ade3227ab5e` |
| SHA-256 | `874c930d246c679c29abd8d7f0400ac50d02af1a46cbf63a83e5060482ac05f0` |

The port patches the game code at fixed addresses, so only version 1.00.00 works. Another copy of 1.00.00 can have a different whole-file hash and still work. What must match is the executable inside it:

| File inside the IPA | Size | SHA-256 |
|---|---|---|
| `Payload/MarvelCap2Us.app/MarvelCap2Us` | 3,021,776 bytes | `2a2c6512c1279cb9b0edcabce99d1b356cc647b29ccbf58865ad75a3424d5ec5` |

It must be decrypted. The port checks its `LC_UUID` (`b58c5f30-3c03-3e1a-9d46-7f34387fb9e6`) and stops with a message if it is a different build.

## Installation

1. In Settings > HENkaku Settings, turn on **Enable unsafe homebrew**.
2. Install kubridge and libshacccg.suprx (see Requirements) and reboot.
3. Install `mvc2.vpk` with VitaShell.
4. Create the folder `ux0:data/mvc2/`.
5. Copy your `.ipa` into that folder. Any file name that ends in `.ipa` works, for example:

   ```
   ux0:data/mvc2/Marvel VS Capcom 2.ipa
   ```

6. Start **Marvel vs. Capcom 2** from the LiveArea.


## Unlocked content

All 56 characters, their extra colors, the stages and the gallery artwork of the Secret Factor are unlocked from the first start. The shop shows every item as already obtained. The game saves this like a normal purchase.

To play with the original locks, create an empty file named `nounlock` in `ux0:data/mvc2/` before the first start. Content already saved as unlocked stays unlocked.


## Known issues and limitations

- Bluetooth versus (GameKit), Twitter and Facebook do not work.
- A few iOS screens (VS MODE's Bluetooth notice, the score attack ranking pages) only have Select (back) besides touch.

## Troubleshooting

- For any other problem, open an issue and attach `ux0:data/mvc2/log.txt`. If the Vita shows an error and writes a crash dump (`ux0:data/*.psp2dmp`), attach it too.

## Credits

- **Capcom** and **Marvel**: Marvel vs. Capcom 2.
- **Rinnegatamante**: vitaGL, vitaShaRK and ShaRKBR33D.
- **bythos14**: kubridge.
- **Sean Barrett**: stb_image.
- **David Reid**: dr_mp3 and dr_wav.
- **itsjustflan**: For testing and reporting issues. 
- **The VitaSDK team.**

## Legal

This project is not affiliated with or endorsed by Capcom or Marvel. No game code or data is included or distributed. Use a copy of the game that you own.
