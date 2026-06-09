# TT9 Bopomofo (中文/注音) — backup

`tt9-bopomofo-zhuyin.apk` — full-debug build of sspanak/tt9 branch `bopomofo-dictionary`
with 3 edits: applicationIdSuffix '.bopomofo', ChineseBopomofo renamed to 中文/注音,
ChineseBopomofoLarge deleted. Package id: io.github.sspanak.tt9.bopomofo (debug-signed).

Install:  adb install -r tt9-bopomofo-zhuyin.apk
Then:     adb shell ime enable  io.github.sspanak.tt9.bopomofo/io.github.sspanak.tt9.ime.TraditionalT9
          adb shell ime set     io.github.sspanak.tt9.bopomofo/io.github.sspanak.tt9.ime.TraditionalT9
Keymap (medials on 0): 中=5-0-9  你=2-0  好=3-8  孫=6-0-9 ; long-press 1=punctuation, 0=space/lang.
Rebuild: clone the branch, apply source-changes.diff, JDK21 + ./gradlew :app:assembleFullDebug.
