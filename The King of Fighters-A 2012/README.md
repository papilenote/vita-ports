# The King of Fighters-A 2012 for PS Vita

Unofficial PS Vita port of the Android version of **THE KING OF FIGHTERS-A 2012** (SNK).

The port is a loader. It runs the game's own Android ARM code natively on the Vita, with the Android system parts (Java side, libc, OpenGL ES, OpenSL ES, the movie player) replaced by Vita code. **No game files are included.** You need your own copy of the Android APK and its OBB expansion file.

| | |
|---|---|
| Title ID | `KOFA00001` |
| Version | 1.0 |
| Status | Tested and played to the end on a real PS Vita, and on Vita3K |
| Download | [`kof2012.vpk`](kof2012.vpk) |

VPK SHA-256: `bb35c5a167daacdb859057b75658b08a4c342f253b0f9ced97abea3a6aa6dc2e`

## Requirements

- A PS Vita with HENkaku (Ensō or h-encore). A PS TV was not tested.
- **Enable unsafe homebrew** turned on in Settings > HENkaku Settings. The port is unsafe homebrew because it uses kubridge. VitaShell warns that it "requests extended permissions" when you install it.
- **kubridge** v0.3.1 or later by bythos14 ([releases](https://github.com/bythos14/kubridge/releases)):
  1. Copy `kubridge.skprx` to `ur0:tai/`.
  2. Under `*KERNEL` in `ur0:tai/config.txt`, add the line `ur0:tai/kubridge.skprx`. If you have `ux0:tai/config.txt`, taiHEN uses that file instead, so add the line there.
  3. Reboot.
- **libshacccg.suprx** (Sony's shader compiler) in `ur0:data/` or `ur0:data/external/`. Extract it with [ShaRKBR33D](https://github.com/Rinnegatamante/ShaRKBR33D) or ShaRKF00D.
- Your own **Android APK** of the game, version 1.0.8, and its **OBB** file.
- About 1.3 GB free on `ux0:` (the APK is 25 MB, the OBB 1.2 GB). The port reads both in place: nothing is unpacked.

The port tells you on screen if kubridge, libshacccg.suprx, the APK or the OBB is missing.

## The game files

**APK**

| | |
|---|---|
| Package | `com.snkplaymore.kof2012a` |
| Version | 1.0.8 |
| Size | 25,652,811 bytes |
| MD5 | `f18f878e1c737ac744face2036e81749` |
| SHA-1 | `c97ca53f230ebea2fe6c42f470b473552b90bb59` |
| SHA-256 | `2addbc7edcb06932a93a19cf1428f58379c0748ac9c24b84afcedb3081c269e4` |

The port hooks the game code by name and at a few fixed addresses, so only version 1.0.8 works. Another copy of 1.0.8 can have a different whole-file hash and still work. What must match is the library inside it:

| File inside the APK | Size | SHA-256 |
|---|---|---|
| `lib/armeabi-v7a/libmain.so` | 4,780,272 bytes | `66726afa4400c2da057e8a7aef11c8768477def372e0e84f83f0887745c1dcca` |

**OBB** (on your phone in `Android/obb/com.snkplaymore.kof2012a/`)

| | |
|---|---|
| File | `main.11.com.snkplaymore.kof2012a.obb` |
| Size | 1,200,664,632 bytes |
| MD5 | `52c7603b18d01e2ecb42ec12bef47370` |
| SHA-256 | `99bf0331c634b2fbee9c4ea45f645d305933c99a1d00b40361317f92fb1e6dcd` |

## Installation

1. In Settings > HENkaku Settings, turn on **Enable unsafe homebrew**.
2. Install kubridge and libshacccg.suprx (see Requirements) and reboot.
3. Install `kof2012.vpk` with VitaShell.
4. Create the folder `ux0:data/kof2012/`.
5. Copy your APK and the OBB into that folder. Any APK file name that ends in `.apk` works, for example:

   ```
   ux0:data/kof2012/KOF-A-2012-v1-0-8.apk
   ux0:data/kof2012/main.11.com.snkplaymore.kof2012a.obb
   ```

6. Start **KOF-A 2012** from the LiveArea.

## Settings screen

A settings screen opens before the game starts:

| Setting | Values |
|---|---|
| FPS | **60** (smooth motion: the fighters are drawn between the game's 20 frames a second) or 20 (as on Android) |
| WIDESCREEN | **ON** (fills the screen) or OFF (the original 3:2 picture with black bars) |
| SHOW TOUCH ICONS | **OFF** or ON (the on-screen buttons in fights; touching the screen works either way) |
| CONTROLS | **XPERIA** or CLASSIC (see Controls) |
| UNLOCKED CONTENT | **ON** or OFF |
| LANGUAGE | **AUTO** (the language set in the game's own OPTION menu; a new save takes the system's), or English, Japanese, Chinese (simplified), Chinese (traditional), French, Italian, German or Spanish, set at every start |

Tick **Don't show this again at startup** to skip it next time. Hold **SELECT** while the game starts to see it again. The choices are kept in `ux0:data/kof2012/conf.ini`.

## Controls

**Xperia** (default): SNK's own layout for the Xperia PLAY keypad, one punch and one kick, as on Android.

| Button | Action |
|---|---|
| D-pad / left stick | Move |
| Cross | P (punch) |
| Circle | K (kick) |
| Square | E (evade) |
| Triangle | S (special: blowback, simple special moves) |
| Square + Cross | HD mode |
| R or SELECT | Super special move |
| L | NEO MAX |
| START | Pause |

**Classic**: KOF's four attack buttons.

| Button | Action |
|---|---|
| D-pad / left stick | Move |
| Square | Light punch |
| Triangle | Heavy punch |
| Cross | Light kick |
| Circle | Heavy kick |
| Cross + Triangle (together) | HD mode (B + C, as in KOF XIII) |
| L | Evade |
| R | Blowback |
| L + R | NEO MAX |
| SELECT | Super special move |
| START | Pause |


## Known issues and limitations

- Bluetooth versus do not work.

## Troubleshooting

The log is off by default. For any problem, set `logs=1` in `ux0:data/kof2012/conf.ini`, play until the problem happens again, then open an issue and attach `ux0:data/kof2012/log.txt` and `log_prev.txt` (the run before). If the game froze, also attach `hang_prev.txt`: the port writes it when the game stops moving (with the log on or off) and copies it there at the next start.

## Credits

- **SNK**: THE KING OF FIGHTERS-A 2012.
- **TheOfficialFloW**: so_util. The loader follows its layout.
- **Rinnegatamante**: vitaGL, vitaShaRK and ShaRKBR33D.
- **bythos14**: kubridge.
- **Sean Barrett**: stb_truetype.
- **DF**: testing and reporting issues.
- **The VitaSDK team.**

## Legal

This project is not affiliated with or endorsed by SNK. No game code or data is included or distributed. Use a copy of the game that you own.