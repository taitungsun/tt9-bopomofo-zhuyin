# TT9 Bopomofo (中文/注音)

官方 TT9 內建拼音（簡體中文），注音輸入的程式碼已存在但尚未正式開放。
此版本基於上游 [`bopomofo-dictionary`](https://github.com/sspanak/tt9/tree/bopomofo-dictionary)
分支，將注音功能啟用並打包為獨立 APK，適用於實體數字鍵盤手機（如 Qin F21 Pro）。

The official TT9 ships Pinyin (Simplified Chinese); Bopomofo exists in the upstream code
but is gated behind `.hidden` files. This build activates and packages it.  
Package id: `io.github.sspanak.tt9.bopomofo` (debug-signed) — installs alongside official TT9.

## 示範影片 / Demo

[![TT9 Bopomofo demo on Qin F21 Pro](https://img.youtube.com/vi/GJ0BOuMyWZ0/0.jpg)](https://youtu.be/GJ0BOuMyWZ0)

## 安裝 / Install

Download the APK from [Releases](../../releases), verify the SHA-256, then:

```sh
adb install -r tt9-bopomofo-zhuyin.apk
adb shell ime enable io.github.sspanak.tt9.bopomofo/io.github.sspanak.tt9.ime.TraditionalT9
adb shell ime set    io.github.sspanak.tt9.bopomofo/io.github.sspanak.tt9.ime.TraditionalT9
```

Quick examples (medials on 0, no tone input needed):  
中=5-0-9 · 你=2-0 · 好=3-8 · 孫=6-0-9 · long-press 1=punctuation, 0=space/lang

## 注音鍵盤配置 / Keypad layout

Non-standard arrangement: the three medials ㄧㄨㄩ sit on **key 0** (not key 7 as on the
classic Taiwan phone layout); initials fill 1–6 and finals fill 7–9.

| Key | 注音 symbols | Sound |
|-----|-------------|-------|
| **1** | ㄅ ㄆ ㄇ ㄈ | b p m f · *(long-press = punctuation)* |
| **2** | ㄉ ㄊ ㄋ ㄌ | d t n l |
| **3** | ㄍ ㄎ ㄏ | g k h |
| **4** | ㄐ ㄑ ㄒ | j q x |
| **5** | ㄓ ㄔ ㄕ ㄖ | zh ch sh r |
| **6** | ㄗ ㄘ ㄙ | z c s |
| **7** | ㄚ ㄛ ㄜ ㄝ | a o e ê |
| **8** | ㄞ ㄟ ㄠ ㄡ | ai ei ao ou |
| **9** | ㄢ ㄣ ㄤ ㄥ ㄦ | an en ang eng er |
| **0** | ㄧ ㄨ ㄩ | i(yi) u(wu) ü(yu) · *(+ space/lang)* |

Tones are **not** keyed — `filterBySounds` predicts candidates from the consonant+vowel
sequence (classic T9), so you pick the character from the candidate list.

Examples: 媽 ㄇㄚ = 1‑7 · 你 ㄋㄧ = 2‑0 · 好 ㄏㄠ = 3‑8 · 中 ㄓㄨㄥ = 5‑0‑9 · 孫 ㄙㄨㄣ = 6‑0‑9

## 重新編譯 / Rebuild

Clone the `bopomofo-dictionary` branch, apply `source-changes.diff`, then:

```sh
./gradlew :app:assembleFullDebug  # requires JDK 21
```

The 3 edits in `source-changes.diff`: `applicationIdSuffix '.bopomofo'`,
`ChineseBopomofo` renamed to `中文/注音`, `ChineseBopomofoLarge` deleted.

## 授權 / License & credit

This is a **derivative work of [sspanak/tt9](https://github.com/sspanak/tt9)** (branch
`bopomofo-dictionary`), licensed under the **GNU GPL v3**. Accordingly this repo is also
released under **GPLv3** — see [`LICENSE`](LICENSE). The modifications are captured in
[`source-changes.diff`](source-changes.diff); the prebuilt APK is not redistributed here
(see its SHA-256 and the rebuild steps above). All credit for TT9 goes to its upstream
authors; this repo only adds a Bopomofo/注音 build config and documentation.
