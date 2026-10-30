# DJMAX Ray for PS Vita

Unofficial PS Vita port of the iOS version of **DJMAX Ray** (Neowiz / Pentavision).

The port is a loader. It runs the game's own iOS ARM code natively on the Vita, with the iOS system parts (Objective-C runtime, Foundation, UIKit, CoreGraphics, OpenGL ES, OpenAL, AudioToolbox) replaced by Vita code. **No game files are included.** You need your own copy of the iOS app (`.ipa`).

| | |
|---|---|
| Title ID | `DJMR00001` |
| Version | 1.0 |
| Status | Beta, tested on Vita3K. Not tested on a real PS Vita yet. |
| Download | [`djmaxray.vpk`](djmaxray.vpk) |

VPK SHA-256: `615090e74873c06286fd4b63efc38744f6ffbaa948f1a044130ac07588626057`


## Requirements

- A PS Vita or PS TV with HENkaku (Ensō, h-encore or HENlo).
- **Enable unsafe homebrew** turned on in Settings > HENkaku Settings. The port is unsafe homebrew because it uses kubridge. VitaShell warns that it "requests extended permissions" when you install it.
- **kubridge** v0.3.1 or later by bythos14 ([releases](https://github.com/bythos14/kubridge/releases)):
  1. Copy `kubridge.skprx` to `ur0:tai/`.
  2. Under `*KERNEL` in `ur0:tai/config.txt`, add the line `ur0:tai/kubridge.skprx`. If you have `ux0:tai/config.txt`, taiHEN uses that file instead, so add the line there.
  3. Reboot.
- **libshacccg.suprx** (Sony's shader compiler) in `ur0:data/` or `ur0:data/external/`. Extract it with [ShaRKBR33D](https://github.com/Rinnegatamante/ShaRKBR33D) or ShaRKF00D.
- Your own **iOS `.ipa`** of the game, version 1.0.11 (decrypted).
- About 2 GB free on `ux0:` for the first start: the `.ipa` (952 MB) and the unpacked game (`iMP.app`: 982 MB in 39,427 files). The `.ipa` is deleted after it is unpacked, which leaves about 1 GB in use.

## The IPA

| | |
|---|---|
| Bundle | `com.neowizInternet.game.djmaxray` (`iMP.app`, shown as "DJMAX Ray") |
| Version | 1.0.11 (build 1.3.23, minimum iOS 7.0) |
| Size | 951,785,790 bytes |
| MD5 | `2e31e90f406b940ec0fd6c8c3aca8b78` |
| SHA-1 | `87eea7a4e2ee165a3d0cd1b25b690fea8eab6c72` |
| SHA-256 | `df52243fc735de646edb3843fcd63981127dc396aa7bc6e1fd3bf1922ea962c7` |

The port hooks the game code at fixed addresses, so only version 1.0.11 works. Another copy of 1.0.11 can have a different whole-file hash and still work. What must match is the executable inside it:

| File inside the IPA | Size | SHA-256 |
|---|---|---|
| `Payload/iMP.app/iMP` | 2,499,824 bytes | `b69541c72d8494932aa1cb3ae2a0fdd0e3cee70532c0faff57d7962754102903` |

It must be decrypted: `cryptid` 0 in its `LC_ENCRYPTION_INFO`. Its `LC_UUID` is `0a649e8e-3583-332b-affa-981da735b66d`.

## Installation

1. In Settings > HENkaku Settings, turn on **Enable unsafe homebrew**.
2. Install kubridge and libshacccg.suprx (see Requirements) and reboot.
3. Install `djmaxray.vpk` with VitaShell.
4. Create the folder `ux0:data/djmaxray/`.
5. Copy your `.ipa` into that folder. Any file name that ends in `.ipa` works, for example:

   ```
   ux0:data/djmaxray/DJMAX Ray.ipa
   ```

6. Start **DJMAX Ray** from the LiveArea. The first start unpacks the game from the `.ipa` into `ux0:data/djmaxray/iMP.app` and then deletes the `.ipa`. This takes several minutes, with a progress bar. If it is interrupted, the next start goes on where it stopped.

The port also looks for the `.ipa` in `ur0:data/djmaxray/`. Instead of the `.ipa`, you can copy its `Payload/iMP.app` folder to `ux0:data/djmaxray/iMP.app`.

The saves and preferences are written to `ux0:data/djmaxray/home/`.

## Troubleshooting

For any problem, open an issue and attach `ux0:data/djmaxray/log.txt` (it is written again at each start). Say what you were doing: which screen, and after which touch.

## Credits

- **Neowiz / Pentavision**: DJMAX Ray.
- **Rinnegatamante**: vitaGL, vitaShaRK and ShaRKBR33D.
- **bythos14**: kubridge.
- **Sean Barrett**: stb_image.
- **David Reid**: dr_mp3.
- **The VitaSDK team.**

## Legal

This project is not affiliated with or endorsed by Neowiz or Pentavision. No game code or data is included or distributed. Use a copy of the game that you own.
