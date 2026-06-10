# TT9 Bopomofo (中文/注音) — backup

`tt9-bopomofo-zhuyin.apk` — full-debug build of sspanak/tt9 branch `bopomofo-dictionary`
with 3 edits: applicationIdSuffix '.bopomofo', ChineseBopomofo renamed to 中文/注音,
ChineseBopomofoLarge deleted. Package id: io.github.sspanak.tt9.bopomofo (debug-signed).

Install:  adb install -r tt9-bopomofo-zhuyin.apk
Then:     adb shell ime enable  io.github.sspanak.tt9.bopomofo/io.github.sspanak.tt9.ime.TraditionalT9
          adb shell ime set     io.github.sspanak.tt9.bopomofo/io.github.sspanak.tt9.ime.TraditionalT9
Keymap (medials on 0): 中=5-0-9  你=2-0  好=3-8  孫=6-0-9 ; long-press 1=punctuation, 0=space/lang.
Rebuild: clone the branch, apply source-changes.diff, JDK21 + ./gradlew :app:assembleFullDebug.

## Keypad layout (注音 / Bopomofo)

Non-standard arrangement: the three medials ㄧㄨㄩ sit on **key 0** (not key 7 as on the
classic Taiwan phone layout); initials fill 1–6 and finals fill 7–9. Source of truth =
the app's own `assets/languages/definitions.yml` (`layout:` block).

| Key | 注音 symbols | Sound |
|-----|-------------|-------|
| **1** | ㄅ ㄆ ㄇ ㄈ | b p m f  · *(long-press = punctuation)* |
| **2** | ㄉ ㄊ ㄋ ㄌ | d t n l |
| **3** | ㄍ ㄎ ㄏ | g k h |
| **4** | ㄐ ㄑ ㄒ | j q x |
| **5** | ㄓ ㄔ ㄕ ㄖ | zh ch sh r |
| **6** | ㄗ ㄘ ㄙ | z c s |
| **7** | ㄚ ㄛ ㄜ ㄝ | a o e ê |
| **8** | ㄞ ㄟ ㄠ ㄡ | ai ei ao ou |
| **9** | ㄢ ㄣ ㄤ ㄥ ㄦ | an en ang eng er |
| **0** | ㄧ ㄨ ㄩ | i(yi) u(wu) ü(yu)  · *(+ space/lang)* |

Tones are **not** keyed — `filterBySounds` predicts candidates from the consonant+vowel
sequence (classic T9), so you pick the character from the candidate list.

Examples: 媽 ㄇㄚ = 1‑7 · 你 ㄋㄧ = 2‑0 · 好 ㄏㄠ = 3‑8 · 中 ㄓㄨㄥ = 5‑0‑9 · 孫 ㄙㄨㄣ = 6‑0‑9
