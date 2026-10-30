# Resident Evil Degeneration for PS Vita

Unofficial PS Vita port of the Android version of **Resident Evil Degeneration** (Capcom).

The port is a loader. It runs the game's own Android ARM code natively on the Vita, with the Android system parts (Java side, libc, OpenGL ES) replaced by Vita code. **No game files are included.** You need your own copy of the Android APK.

| | |
|---|---|
| Title ID | `REDG00001` |
| Version | 1.0 |
| Status | Tested and played on a real PS Vita and on Vita3K. |
| Download | [`redegeneration.vpk`](redegeneration.vpk) |

VPK SHA-256: `a8d20b47b482ddb4b55eaed3c327dae57379c6a84a88e866932b397e3e331598`


## Requirements

- A PS Vita with HENkaku (Ensō or h-encore). A PS TV was not tested.
- **Enable unsafe homebrew** turned on in Settings > HENkaku Settings. The port is unsafe homebrew because it uses kubridge and kernel calls. VitaShell warns that it "requests extended permissions" when you install it.
- **kubridge** v0.3.1_hotfix by bythos14 ([releases](https://github.com/bythos14/kubridge/releases)):
  1. Copy `kubridge.skprx` to `ur0:tai/`.
  2. Under `*KERNEL` in `ur0:tai/config.txt`, add the line `ur0:tai/kubridge.skprx`. If you have `ux0:tai/config.txt`, taiHEN uses that file instead, so add the line there.
  3. Reboot.
- **libshacccg.suprx** (Sony's shader compiler) in `ur0:data/` or `ur0:data/external/`. Extract it with [ShaRKBR33D](https://github.com/Rinnegatamante/ShaRKBR33D) or ShaRKF00D.
- Your own **Android APK** of the game, version 1.00.03.

## The APK

| | |
|---|---|
| Package | `jp.co.capcom.android.jirobiodg` |
| Version | 1.00.03 (versionCode 1000003) |
| Size | 20,001,777 bytes |
| MD5 | `e9f56353e0031d490b808f4a4739faac` |
| SHA-1 | `70b4dcd1429602fb09d744a8bdcc7d335ac6fa30` |
| SHA-256 | `6654b4af083a899b5c75de92a66b485435b3ce6ac65afbe96082d5ede4eb23d2` |

The port patches the game code at fixed addresses, so only version 1.00.03 works. The tested APK is itself a re-signed copy, so another copy of 1.00.03 can have a different whole-file hash and still work.

What must match are these two files inside the APK:

| File inside the APK | Size | SHA-256 |
|---|---|---|
| `lib/armeabi/libjirobiodg.so` | 431,528 bytes | `ce6c9f6f7339f226c1f060744ddb89d7b187d01a8b20571cd417896bf4c4fcf0` |
| `assets/biohazard.s3e` | 673,661 bytes | `3b673d9e88071ad6a83ff892eef394447cf4cb81e540a11ae31f9265a181c271` |

The rest of `assets/` must also be the original game files: `main.dz`, `app.icf`, `s3e.icf` and `intro.mp4`.

## Installation

1. In Settings > HENkaku Settings, turn on **Enable unsafe homebrew**.
2. Install kubridge and libshacccg.suprx (see Requirements) and reboot.
3. Install `redegeneration.vpk` with VitaShell.
4. Create the folder `ux0:data/redegeneration/`.
5. Copy your APK into that folder. Any file name that ends in `.apk` works, for example:

   ```
   ux0:data/redegeneration/Resident Evil Degeneration Android.apk
   ```

6. Start **RE Degeneration** from the LiveArea.

If the APK is not in `ux0:data/redegeneration/`, the port also looks in `ur0:data/redegeneration/`, `ux0:data/` and `ur0:data/`. It uses the first `.apk` that contains `assets/biohazard.s3e`.


## Known issues and limitations

- **Beta.** It is not yet confirmed that the whole game can be completed on the Vita.

## Troubleshooting

For any other problem, open an issue and attach `ux0:data/redegeneration/log.txt`.

## Credits

- **Capcom**: Resident Evil Degeneration.
- **TheOfficialFloW**: so_util. The loader follows its layout.
- **Rinnegatamante**: vitaGL and ShaRKBR33D.
- **bythos14**: kubridge.
- **David Reid**: dr_mp3 and dr_wav.
- **The VitaSDK team.**

## Legal

This project is not affiliated with or endorsed by Capcom. No game code or data is included or distributed. Use a copy of the game that you own.