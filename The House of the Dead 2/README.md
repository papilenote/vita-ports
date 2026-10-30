# The House of the Dead 2 for PS Vita

Unofficial **The House of the Dead 2** (Sega) port.

| | |
|---|---|
| Title ID | `HOTD20001` |
| Version | 1.0 |
| Status | Tested and played on a real PS Vita and on Vita3K. |
| Download | [`hotd2.vpk`](hotd2.vpk) |

VPK SHA-256: `55c79f108eb5a0afd410385fd6222ec9111ac1567751061117d9194bfe0d46db`


## Requirements

- A PS Vita with HENkaku (Ensō or h-encore). A PS TV was not tested.
- **Enable unsafe homebrew** turned on in Settings > HENkaku Settings. The port is unsafe homebrew because vitaGL loads the shader compiler. VitaShell warns that it "requests extended permissions" when you install it.
- **libshacccg.suprx** (Sony's shader compiler) in `ur0:data/` or `ur0:data/external/`. Extract it with [ShaRKBR33D](https://github.com/Rinnegatamante/ShaRKBR33D) or ShaRKF00D.
- The **game data** of the PC version of The House of the Dead 2.
- About 550 MB free on `ux0:`.

kubridge is not needed.

## The game data

The `game` folder of the PC version: `Hod2.exe` with the folders `cam`, `coli`, `evt`, `mot`, `pol`, `sound` and `tex`.

| | |
|---|---|
| Files | 2,042 (546,168,750 bytes) |
| `Hod2.exe` | 1,699,840 bytes |
| `Hod2.exe` SHA-256 | `c6b4116788b7f68c56860fb9cc8a94bf984e620907031e4bc3db43623dbe579a` |


## Installation

1. In Settings > HENkaku Settings, turn on **Enable unsafe homebrew**.
2. Install libshacccg.suprx (see Requirements).
3. Install `hotd2.vpk` with VitaShell.
4. Copy the game folder to `ux0:data/hotd2/`, so that this file exists:

   ```
   ux0:data/hotd2/game/Hod2.exe
   ```

5. Start **The House of the Dead 2** from the LiveArea.

The settings, records and saves are written to `ux0:data/hotd2/`.

## Troubleshooting

For any problem, open an issue and attach `ux0:data/hotd2/log.txt`.

## Credits

- **Sega**: The House of the Dead 2.
- **GitFist**: HOTD2RE (MIT license), the native rebuild this port runs.
- **Rinnegatamante**: vitaGL, vitaShaRK and ShaRKBR33D.
- **The VitaSDK team.**

## Legal

This project is not affiliated with or endorsed by Sega. No game data is included or distributed. Use a copy of the game that you own.
