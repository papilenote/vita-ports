# The Simpsons Arcade for PS Vita

Unofficial PS Vita port of the iOS version of **The Simpsons Arcade** (EA Mobile).

The port is a loader. It runs the game's own iOS ARM code natively on the Vita, with the iOS system parts (Objective-C runtime, Foundation, UIKit, CoreGraphics, OpenGL ES, OpenAL and AudioQueue) replaced by Vita code. **No game files are included.** You need your own copy of the iOS `.ipa`.

| | |
|---|---|
| Title ID | `SMPA00001` |
| Version | 1.1 |
| Status | Tested on a real PS Vita and on Vita3K |
| Download | [`simpsons.vpk`](simpsons.vpk) |

VPK SHA-256: `db4d0fea37215ac45eb0d4349de12c84f6b51ed3d776a4107c498b90ef33d34b`

## Requirements

- A PS Vita with HENkaku (Ensō or h-encore). A PS TV was not tested.
- **Enable unsafe homebrew** turned on in Settings > HENkaku Settings. The port is unsafe homebrew because it uses kubridge. VitaShell warns that it "requests extended permissions" when you install it.
- **kubridge** by bythos14 ([releases](https://github.com/bythos14/kubridge/releases)):
  1. Copy `kubridge.skprx` to `ur0:tai/`.
  2. Under `*KERNEL` in `ur0:tai/config.txt`, add the line `ur0:tai/kubridge.skprx`. If you have `ux0:tai/config.txt`, taiHEN uses that file instead, so add the line there.
  3. Reboot.
- **libshacccg.suprx** (Sony's shader compiler) in `ur0:data/` or `ur0:data/external/`. Extract it with [ShaRKBR33D](https://github.com/Rinnegatamante/ShaRKBR33D) or ShaRKF00D.
- Your own **decrypted `.ipa`** of the game, version 1.1.43.
- About 130 MB free on `ux0:` (the `.ipa` is 51 MB, the game it unpacks 66 MB).

The port tells you on screen if kubridge, libshacccg.suprx or the game is missing.

## The .ipa

| | |
|---|---|
| Bundle ID | `com.ea.simpsonsarcade.bv` |
| Version | 1.1.43 |
| Size | 53,319,874 bytes |
| MD5 | `8846c70cc2c464582d60984e30580e8d` |
| SHA-256 | `f48b04ee4b0c2349d2898190e16bd29bb6dfa6e6fd43ad11496ae3432574ee1d` |

The port patches the game code at fixed addresses, so only version 1.1.43 works. Another copy of 1.1.43 can have a different whole-file hash and still work. What must match is the executable inside it:

| File inside the .ipa | Size | SHA-256 |
|---|---|---|
| `Payload/simpsons3_iphone_en.app/simpsons3_iphone_en` | 1,917,632 bytes | `6d1624f17bd1338d011fa2904694365c59aa2fb756c4845767462ae1ee04851c` |

## Installation

1. In Settings > HENkaku Settings, turn on **Enable unsafe homebrew**.
2. Install kubridge and libshacccg.suprx (see Requirements) and reboot.
3. Install `simpsons.vpk` with VitaShell.
4. Create the folder `ux0:data/thesimpsonsarcade/`.
5. Copy your `.ipa` into that folder. Any file name that ends in `.ipa` works, for example:

   ```
   ux0:data/thesimpsonsarcade/The Simpsons Arcade v1.1.43.ipa
   ```

6. Start **The Simpsons Arcade** from the LiveArea. The first start unpacks the game into `ux0:data/thesimpsonsarcade/simpsons3_iphone_en.app`, then the port restarts by itself. After that you can delete the `.ipa`.


## Known issues and limitations

- **MUSIC LIBRARY** is an iOS feature (the iPod music library) and does nothing useful on the Vita.
- Online features (EA's servers) do not work.

## Troubleshooting

For any problem, open an issue and attach `ux0:data/thesimpsonsarcade/log.txt`. It is written at every start and covers the last run, so copy it right after the problem happens.

## Credits

- **EA Mobile / 20th Century Fox**: The Simpsons Arcade.
- **Rinnegatamante**: vitaGL, vitaShaRK and ShaRKBR33D.
- **bythos14**: kubridge.
- **Sean Barrett**: stb_truetype, stb_image.
- **David Reid**: dr_mp3, dr_wav.
- **The VitaSDK team.**

## Legal

This project is not affiliated with or endorsed by Electronic Arts or 20th Century Fox. No game code or data is included or distributed. Use a copy of the game that you own.