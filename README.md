# Vita Ports

Unofficial PS Vita ports, ready to install. Each folder holds one game's VPK and a README with its requirements, install steps and controls.

No game data is included. You need your own copy of each game.

| Game | Based on | Title ID | Version | Status |
|---|---|---|---|---|
| [DJMAX Ray](DJMAX%20Ray/) | iOS IPA 1.0.11 | `DJMR00001` | 1.0 | tested on PSVITA and Vita3K |
| [Marvel vs. Capcom 2](Marvel%20VS%20Capcom%202/) | iOS IPA 1.00.00 | `MVSC00001` | v1.0 | ested on PSVITA and Vita3K  |
| [Resident Evil Degeneration](Resident%20Evil%20Degeneration/) | Android APK 1.00.03 | `REDG00001` | 1.0 | tested on PSVITA and Vita3K |
| [Resident Evil Mercenaries VS](Resident%20Evil%20Mercenaries%20VS/) | iOS IPA 1.10.10 | `REMV00001` | 0.1 | tested on PSVITA and Vita3K |
| [Tap Sonic](Tap%20Sonic/) | Android APK 1.0.2 | `TPSN00001` | 1.0 | tested on PSVITA and Vita3K |
| [The House of the Dead 2](The%20House%20of%20the%20Dead%202/) | HOTD2RE 1.1 with the PC game data | `HOTD20001` | 1.0 | tested on PSVITA and Vita3K |
| [Vita-ngage](Vita-ngage/) | N-Gage | `NGAG00001` | 0.2 | tested on PSVITA and Vita3K |

## Common requirements

Most ports need:

- a PS Vita or PS TV with HENkaku (Ensō or h-encore), with **Enable unsafe homebrew** turned on;
- **[kubridge](https://github.com/bythos14/kubridge/releases)** (`kubridge.skprx`, bythos14) under `*KERNEL` in `ur0:tai/config.txt`, or in `ux0:tai/config.txt` if you have that file;
- **libshacccg.suprx** in `ur0:data/`, extracted with [ShaRKBR33D](https://github.com/Rinnegatamante/ShaRKBR33D) or ShaRKF00D.

Check each game's README for its exact requirements.

## Reporting a problem

Open an issue with:

- the game.
- what happened.
- the log file named in that game's README.