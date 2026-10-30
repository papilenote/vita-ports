# Tap Sonic for PS Vita

Unofficial PS Vita port of the Android version of **Tap Sonic** (Neowiz).

The port is a loader. It runs the game's own Android ARM code natively on the Vita, with the Android system parts (Java side, libc, OpenGL ES, sound player) replaced by Vita code. The Java menus are rebuilt with the APK's own pictures. **No game files are included.** You need your own copy of the Android APK and of its songs.

| | |
|---|---|
| Title ID | `TPSN00001` |
| Version | 1.0 |
| Status | Tested and played on a real PS Vita and on Vita3K. |
| Download | [`tapsonic.vpk`](tapsonic.vpk) |

VPK SHA-256: `2aed275152d3f2abb05e71f2e817cc8e822a37583f9845a70f53fc1240a4a124`


## Requirements

- A PS Vita or PS TV with HENkaku (Ensō, h-encore or HENlo).
- **Enable unsafe homebrew** turned on in Settings > HENkaku Settings. The port is unsafe homebrew because it uses kubridge. VitaShell warns that it "requests extended permissions" when you install it.
- **kubridge** v0.3.1_hotfix by bythos14 ([releases](https://github.com/bythos14/kubridge/releases)); v0.1 or later works:
  1. Copy `kubridge.skprx` to `ur0:tai/`.
  2. Under `*KERNEL` in `ur0:tai/config.txt`, add the line `ur0:tai/kubridge.skprx`. If you have `ux0:tai/config.txt`, taiHEN uses that file instead, so add the line there.
  3. Reboot.
- **libshacccg.suprx** (Sony's shader compiler) in `ur0:data/` or `ur0:data/external/`. Extract it with [ShaRKBR33D](https://github.com/Rinnegatamante/ShaRKBR33D) or ShaRKF00D.
- Your own **Android APK** of the game, version 1.0.2, and the game's **songs** from your phone (see below).
- About 620 MB free on `ux0:`.

## The APK

| | |
|---|---|
| Package | `co.kr.neowiz.tapsonic` |
| Version | 1.0.2 (versionCode 3) |
| Size | 10,911,628 bytes |
| MD5 | `bb58b3ff8d96443bec3c449eab1fd49a` |
| SHA-1 | `48806b1a90b6e82f479ab5ba58fa36e01d77a8f5` |
| SHA-256 | `c2f23d7a171a21031bcf8668dc3ee377ae35406af79d7c0292785f455a29e56a` |

The port was tested only with version 1.0.2. Another copy of 1.0.2 can have a different whole-file hash (for example, if it was signed again) and still work.

What the port runs and reads are these files inside the APK:

| File inside the APK | Size | SHA-256 |
|---|---|---|
| `lib/armeabi/libgamelib.so` | 546,476 bytes | `9ec769635967925cba50caac1de4acba745afba671718b011c734188b7abb9b4` |
| `lib/armeabi/libplatformlib.so` | 392,636 bytes | `f08e5baf0298365acec14626358c70a9f310cce03fc75d320ae6de001e84a098` |
| `lib/armeabi/libstlport_shared.so` | 277,244 bytes | `c80eac54d0e8660e4c05fbda7e618fbd04d6197fda05930375cdd4a73db5fd4f` |
| `lib/armeabi/libpacklib.so` | 135,220 bytes | `e37aa4dfb79cea19d5c3eef069b9c8fdd0f692595dce6531d89908117eaef6f3` |
| `lib/armeabi/libtinyxml.so` | 80,152 bytes | `12d317a0ea83215570b6c1ea9bc25b275676397715150a771975a97d97ea5b85` |
| `lib/armeabi/libutillib.so` | 54,564 bytes | `38bcc2cb658b4b7ee4d2ff1295c9ed870b4bfded989cede66d39466114021b0b` |
| `lib/armeabi/libscorelib.so` | 42,296 bytes | `819114eb3fcebecb03c6ef073f62cb107a3226d5d46aaf4d917cd8e962ae9541` |
| `lib/armeabi/libwrapper.so` | 21,984 bytes | `4ffe56f46ac9ce53e56a84b4e0f566072b417c2d53745e630cfc18eb957a324c` |
| `assets/ingame_data.pak` | 920,864 bytes | `9f5afaa05d0f5aeb2e3aa802a361d327de8902492839a036c2c7c2d968241704` |
| `assets/default_skin.pak` | 602,059 bytes | `7a78f56cf5eb937b47d873418cf9d98565549ed1f2a5baf99ff0f31992fd7e77` |
| `assets/outgame_data.pak` | 128 bytes | `9b94683cd875dcf5fd99915dea3860744d545390a03cdd155a6553e0f8952291` |

The menus also use the APK's pictures and sounds in `res/drawable-mdpi/` and `res/raw/`.

To get the APK, back up the installed app from your phone with an APK extractor app, or with `adb shell pm path co.kr.neowiz.tapsonic` followed by `adb pull`.

## The songs

The songs are not in the APK. They are in the folder `/sdcard/.tapsonic/` of the phone where the game downloaded them: about 600 MB with 206 songs, in the folders `song` (the songs), `pak` (the animated backgrounds), `cache` (the covers) and `databases`.


## Installation

1. In Settings > HENkaku Settings, turn on **Enable unsafe homebrew**.
2. Install kubridge and libshacccg.suprx (see Requirements) and reboot.
3. Install `tapsonic.vpk` with VitaShell.
4. Create the folder `ux0:data/tapsonic/`.
5. Copy into that folder your APK (any file name that ends in `.apk` works) and the **contents** of the phone's `.tapsonic` folder:

   ```
   ux0:data/tapsonic/
   ├── Tap Sonic.apk
   ├── song/
   ├── pak/
   ├── cache/
   └── databases/
   ```

   The contents of `.tapsonic` can also stay in their own folder, `ux0:data/tapsonic/.tapsonic/`.

6. Start **Tap Sonic** from the LiveArea. The first start extracts what the port needs from the APK to `ux0:data/tapsonic/apk/` (about 10 MB, a few seconds). The APK can be deleted after that.

If the APK is not in `ux0:data/tapsonic/`, the port also looks in `ur0:data/tapsonic/`, `ux0:data/` and `ur0:data/`, and uses the first `.apk` it finds there. The songs can also be in `ur0:data/tapsonic/`.

The settings, records and log are written to `ux0:data/tapsonic/`.


## Troubleshooting

For any problem, open an issue and attach `ux0:data/tapsonic/log.txt`.

## Credits

- **Neowiz**: Tap Sonic.
- **Rinnegatamante**: vitaGL, vitaShaRK and ShaRKBR33D.
- **bythos14**: kubridge.
- **David Reid**: dr_mp3 and dr_wav.
- **Sean Barrett**: stb_image.
- **SQLite** (public domain).
- **The VitaSDK team.**

## Legal

This project is not affiliated with or endorsed by Neowiz. No game code or data is included or distributed. Use a copy of the game that you own.
