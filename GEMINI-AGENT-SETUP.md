# Setup: TSA-X buat Gemini Agent Mode (Android Studio)

**TL;DR:** 2 file baru — `AGENTS.md` di root project, `docs/tsa/TSA-X-FULL.md` di
folder docs. `AGENTS.md` otomatis ke-scan Gemini tiap kirim prompt (nggak perlu
attach manual kayak `TSA-X.md` lama), isinya sengaja diringkas biar nggak "nge-drown"
Agent Mode kayak kemarin. Kontrak lengkapnya (50 Agreements) dipindah ke
`TSA-X-FULL.md`, dipasang manual cuma pas kerjaan Mode 3.

## Kenapa didesain begini

Dari yang udah kita bahas: Agent Mode di Android Studio itu emang lebih cocok dikasih
instruksi pendek & spesifik ketimbang rulebook 536 baris sekaligus. Google sendiri
juga bilang gitu di dokumentasi resminya — konteks yang terlalu padat malah bikin
Gemini "kesasar", bukan makin nurut.

## Langkah pasang

1. **Taruh `AGENTS.md` di root project** (sejajar `settings.gradle`). Gemini
   otomatis scan file ini (dan `AGENTS.md` di semua folder induk/turunan) setiap
   kali situ kirim prompt — jadi nggak perlu attach ulang tiap sesi kayak workflow
   `TSA-X.md` yang lama.
2. **Taruh `TSA-X-FULL.md` di `docs/tsa/`.** Ini nggak ke-load otomatis — sengaja,
   biar hemat token. Attach manual lewat Context drawer di chat panel Gemini,
   cuma pas situ declare MODE 3 (Foundation) atau butuh full 50 Agreements.
3. **(Opsional tapi disaranin) Setup Rules** di
   `File > Settings > Tools > AI > Prompt Library`, scope **Project**, isi
   1–3 baris aja, misal:
   ```
   Always declare MODE before changing code. Never invent an API — verify
   against Android docs first. Only touch the file/function named in scope.
   ```
   Rules ini nempel di depan *setiap* prompt, jadi harus tetep pendek — beda
   fungsi sama `AGENTS.md` yang lebih panjang/kontekstual.
4. **Cek tier/API key situ** di `Settings > Tools > Gemini`. Kalau pake API key
   pribadi, tambahin API key Gemini sendiri di situ buat dapet Gemini 2.5 Pro +
   context window 1M token — kalau masih pake model default gratis, itu bisa jadi
   penyebab lain hasilnya lebih ngedrop dibanding Copilot CLI, di luar soal
   kontraknya. Kalau situ udah di tier bisnis (lisensi Code Assist), ini otomatis
   dapet tanpa perlu API key.
5. **Kalau ada modul yang butuh rule beda** (misal modul legacy vs modul baru),
   bisa taruh `AGENTS.md` tambahan di subfolder modul itu — Gemini baca semua
   `AGENTS.md` secara hierarkis, yang lebih spesifik ketemu duluan pas kerja di
   folder itu.

## Cara uji

Coba satu task kecil Mode 1 (micro patch) yang sama persis ke Gemini Agent Mode
dan ke Copilot CLI, bandingin hasilnya. Framework situ sendiri prinsipnya
"evolve dari pengalaman nyata" (AG-37) — jadi kalau hasil `AGENTS.md` versi ini
masih kurang nurut, kabarin lagi bagian mana yang meleset, biar diringkas/
disesuaikan lagi. Bukan sekali jadi.

## Push ke repo

Karena `AGENTS.md` itu standar IDE-independent (bukan cuma Android Studio),
naruh ini di root repo `anoramyid/TSA` juga masuk akal — jadi repo situ bisa
"optimized for Claude, ChatGPT, Gemini, Cursor, ..." beneran, bukan cuma klaim
di README.
