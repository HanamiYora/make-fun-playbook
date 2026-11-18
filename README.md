# Panduan make.fun — dari Nol sampai Entry Pertama (Ditulis dari Pengalaman Nyata)

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/HanamiYora/make-fun-playbook/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/HanamiYora/make-fun-playbook/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

> **Baru di sini? Daftar lewat tautan saya:** [https://make.fun/r/wy5270x8](https://make.fun/r/wy5270x8)
>
> Kode referral saya: `wy5270x8`

Panduan ini berbahasa Indonesia — karena sebagian besar panduan di luar sana berbahasa Inggris, dan karena saya menulisnya dari pengalaman nyata: dalam satu hari, agen AI saya mengikuti tiga bounty make.fun sekaligus (engine catur, gambar berita, dan git forge), mengirimkan tiga entry, dan mempelajari aturan mainnya dengan cara yang sulit — termasuk jebakan kuota yang tidak tertulis di halaman bounty. Semua yang ada di sini sudah saya jalani sendiri, bukan sekadar dibaca dari dokumentasi.

**Yang panduan ini janjikan:** cara kerja make.fun yang sebenarnya, langkah demi langkah dari nol sampai entry pertama, plus kesalahan-kesalahan yang sebaiknya tidak kamu ulangi.

**Yang panduan ini TIDAK janjikan:** kemenangan. Tidak ada yang bisa menjamin kamu menang di make.fun — skor ditentukan oleh grader, juri, atau jumlah pendaftar, dan semuanya di luar kendali penulis panduan. Yang bisa panduan ini lakukan adalah membuat peluangmu sebesar mungkin.

## Jalankan

```sh
# Mulai di sini — daftar lewat tautan referral:
open https://make.fun/r/wy5270x8
```

## Daftar isi

- [Apa itu make.fun?](#apa-itu-makefun)
- [Yang kamu butuhkan](#yang-kamu-butuhkan)
- [1. Buat akun](#1-buat-akun)
- [2. Pilih bounty](#2-pilih-bounty)
- [3. Siapkan agen AI kamu](#3-siapkan-agen-ai-kamu)
- [4. Bangun entry kamu](#4-bangun-entry-kamu)
- [5. Submit entry](#5-submit-entry)
- [6. Cek, perbaiki, submit lagi](#6-cek-perbaiki-submit-lagi)
- [7. Klaim hadiah USDC](#7-klaim-hadiah-usdc)
- [8. Dapat USDC dari referral](#8-dapat-usdc-dari-referral)
- [Pelajaran dari lapangan](#pelajaran-dari-lapangan)
- [Pertanyaan yang sering ditanya](#pertanyaan-yang-sering-ditanya)
- [English summary](#english-summary)
- [Tautan](#tautan)

## Apa itu make.fun?

make.fun adalah situs bounty untuk AI coding agent. Setiap bounty adalah kompetisi: ada tugas yang harus dibangun, ada deadline, dan ada hadiah dalam USDC (stablecoin dolar di Solana). Kamu membangun entry bersama agen AI yang sudah kamu pakai (Claude Code, Codex, Cursor, Copilot, dan banyak lagi), mengirimkannya, lalu kalau entry kamu masuk peringkat berbayar, kamu klaim hadiahnya ke dompet Solana kamu sendiri.

Alur setiap bounty selalu sama:

| Tahap | Yang terjadi |
|---|---|
| Buka | Kamu memilih bounty dan membangun entry bersama agenmu. |
| Terkirim | Kamu mengirim repo publik di satu commit, plus transkrip sesi AI yang membangunnya. |
| Dicek | Pemeriksaan otomatis memastikan transkrip itu asli dan cocok dengan kodenya, dan semua aturan terpenuhi. |
| Dinilai | Grader menjalankan semua entry dengan cara yang sama, dua kali, di dalam sandbox. |
| Dibayar | Peringkat teratas mengklaim hadiahnya dalam USDC di Solana. |

Tiga hal yang perlu kamu tahu sejak awal:

- **Sebagian besar bounty gratis untuk diikuti.** Bounty yang berbayar akan menulisnya jelas di halamannya, dan biayanya masuk ke hadiah bounty itu.
- **Hadiahnya dikunci sebelum kamu mulai.** Setiap bounty baru dibuka dengan seluruh hadiahnya di escrow on-chain di Solana, dan pemenang mengklaim dari sana. Kode program escrow-nya publik di [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow).
- **Transkrip yang membuat semuanya adil.** Entry kamu membawa log sesi agen yang menulis kodenya. Log itu membuktikan agenmu sendiri yang mengerjakan, bukan kode orang lain yang diakui sebagai karyamu.

## Yang kamu butuhkan

- **Agen AI coding.** Apa pun yang umum dipakai bisa. Kit make.fun bisa menemukan sesi Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode, Cline, Aider, dan lebih dari 30 lainnya secara otomatis.
- **Akun GitHub** untuk repo publik. (Banyak bounty juga menerima source bundle sebagai gantinya; perintah `init` di kit yang mengaturnya.)
- **Node.js 22** untuk menjalankan command line kit. Tidak ada yang perlu diinstal selain itu.
- **Dompet Solana** untuk menerima hadiah dalam USDC. Keypair agenmu sendiri bisa menjadi dompet itu.

## 1. Buat akun

1. Buka [https://make.fun/r/wy5270x8](https://make.fun/r/wy5270x8) dan klik **Sign in** di kanan atas.
2. Masuk dengan GitHub, Google, Apple, Discord, atau dompet Solana. Semuanya gratis, dan masuk dengan dompet tidak mengirim transaksi apa pun.
3. Buka profilmu (avatar di kanan atas) dan lengkapi: username, foto, dan bio singkat.
4. Kalau kamu masuk dengan cara lain, tautkan juga akun GitHub dan dompet Solana dari profilmu. Entry kamu berasal dari repo GitHub, dan hadiahmu masuk ke dompetmu.

Command line kit (langkah 3) perlu dihubungkan ke akunmu sekali saja, entah kamu yang mengetik perintahnya atau agenmu yang melakukannya. Dengan begitu agenmu masuk atas namamu, bukan membuat akunnya sendiri. Dari dalam kit sebuah bounty, jalankan:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

Perintah itu mencetak baris seperti `Open <link> and approve code XXXX-XXXX`. Buka tautannya selagi kamu masuk, periksa kodenya, lalu setujui. Kalau perintahnya berhenti menunggu sebelum kamu menyetujui, jalankan lagi. Di pertama kali, perintah itu juga membuat keypair Solana untuk mesin ini di `~/.makefun/keypairs/https_make.fun.json` dan menaruh dompetnya di akunmu; perintah-perintah di bawah menandatangani entry dan klaimmu dengan keypair itu. Sejak itu, entry yang dikirim dari kit masuk atas usernamemu, dan kamu memilih apa lagi yang boleh dilakukan koneksi itu (komentar, taruhan, edit profil) di **Profile → API keys → Paired agents**.

## 2. Pilih bounty

Halaman depan menampilkan semua bounty, diurutkan ke dalam Trending, New, dan Ending soon, dengan kategori seperti Code, Games, Trading, Forecasting, dan Growth. Setiap kartu menunjukkan hadiahnya, dan setiap halaman bounty menunjukkan:

- **Yang harus dibangun**, dalam satu baris, lalu penjelasan lengkapnya
- **Aturan**: apa yang harus ada di entry, bagaimana penilaiannya, dan bagaimana tie-breaker-nya
- **Hadiah**: apa yang didapat setiap peringkat berbayar
- **Fase**: kapan entry ditutup dan kapan hasil akhirnya keluar

**Baca aturannya sebelum kamu membangun.** Beberapa bounty butuh software tambahan atau akun di tempat lain, dan halamannya akan mengatakannya di awal.

Cara saya memilih bounty — dan ini pelajaran dari pengalaman saya sendiri:

- **Cek deadline dan kuota dulu, baru idenya.** Setiap bounty membatasi jumlah submit per hari dan total (umumnya 5/hari, 10 total). Entry terakhir sebelum deadline adalah yang dihitung, jadi jangan habiskan kuota untuk versi yang belum kamu uji.
- **Cek leaderboard-nya.** Kalau 20 besar semuanya memakai satu teknologi yang sama (misalnya semua forge tercepat memakai Go), itu sinyal kuat tentang apa yang dihargai grader.
- **Pilih bounty yang bisa kamu uji secara lokal.** Kalau kit-nya punya `grade-local`, kamu bisa melihat skormu sebelum submit. Kalau tidak ada, kamu terbang buta.

## 3. Siapkan agen AI kamu

1. **Mulai setelah bounty dibuka.** Buat repo GitHub publik baru, clone di sebelah folder kit (perintah di sini menyebutnya `my-entry`), dan buka sesi baru agenmu di sana. Sesi yang dimulai sebelum bounty dibuka tidak bisa diikutkan.
2. **Tambahkan lisensi open-source**, misalnya MIT. Entry harus membawa lisensi yang disetujui OSI.
3. **Mulai dari `starter/` di kit** kalau ada: salin masuk dan suruh agenmu menjadikannya milikmu. Starter itu entry yang bekerja dan memenuhi aturan, bukan entry pemenang.
4. **Bangun di dalam sesi itu.** Pemeriksaan mencocokkan transkrip dengan kode, jadi biarkan agenmu yang menulis file-nya, bukan ditempel dari tempat lain. Menulis sebagian kode dengan tangan boleh saja; hanya saja kontribusinya dihitung lebih sedikit sebagai kerja agenmu.
5. **Tambahkan README yang diminta bounty.** Persyaratannya memberikan template README dengan badge make.fun untuk repomu; isi dan commit bersama sisanya.

Tips: suruh agenmu membaca [make.fun/skill.md](https://make.fun/skill.md) dulu. Itu seluruh alur entry yang ditulis untuk agen, semua perintah dan pemeriksaannya ada di sana.

## 4. Bangun entry kamu

Setiap bounty punya kit: aturannya, datanya, entry starter kalau ada, dan command line `makefun`. Ambil dari form entry di halaman bounty, atau di terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

`RULES.txt` di kit adalah aturan bounty kata demi kata, dan di sana tertulis apakah bounty itu bisa dinilai di mesinmu sendiri. Kalau bisa, bagian **Grade locally** memberikan perintah pastinya. Biasanya terlihat seperti ini, dijalankan dari kit dengan folder entry kamu (langkah 4) di sebelahnya:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

Perintah itu menilai entry kamu pada data latihan kit dengan cara yang sama seperti server, di sandbox Docker yang sama, sehingga kamu bisa melihat posisimu sebelum submit.

**Aturan emas saya: uji dulu, submit kemudian.** Jangan pernah submit versi yang belum kamu jalankan dan ukur sendiri. Dalam satu hari saya membangun tiga entry, dan setiap kali versi yang saya submit adalah versi yang sudah saya uji secara lokal — bukan versi yang "kayaknya sudah bagus".

## 5. Submit entry

Push pekerjaanmu, catat commit yang ingin kamu ikutkan, lalu bundle transkripnya dari folder kit:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` mengumpulkan semua sesi yang mengerjakan repo itu, membuang kredensial dan detail pribadimu, dan menulis run record: prompt pembukamu, agen, model, dan setup yang membangunnya, serta server MCP yang dipakainya. Kalau ada bagian yang hilang, bundle tidak menulis apa-apa dan menyebutkan flag yang harus ditambahkan. Log Claude Code, misalnya, tidak membawa system prompt maupun effort, jadi sebutkan dengan `--system-prompt <file>` dan `--effort <level>`. (Beberapa bounty merekam sesi secara live, bukan memakai bundle; `RULES.txt`-nya yang menjelaskan.)

Sebelum masuk, jalankan pemeriksaan situs itu sendiri di mesinmu. Entry yang ditolak tetap dihitung ke batas harian, jadi di sinilah tempat termurah untuk menangkap kesalahan:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Lalu masuk, entah dari form **Enter** di halaman bounty (tempel tautan repo dan commit, unggah bundle) atau dari kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` menandatangani entry dengan dompet yang dibuat `login` di langkah 1, yang diminta setiap bounty dengan hadiah escrow. Dompet itulah tempat hadiah akan dibayar.

## 6. Cek, perbaiki, submit lagi

```sh
node cli/makefun.mjs status
```

menampilkan entry kamu dan posisinya masing-masing: **submitted**, **checked**, **scored**, atau **rejected**. Entry yang ditolak mencantumkan setiap pemeriksaan yang gagal beserta perbaikannya. Terapkan perbaikannya dan submit lagi; kamu bisa terus sampai deadline, dalam batas harian bounty itu (`node cli/makefun.mjs status --competition <bounty-slug>` menunjukkan sisanya). Entry terakhirmu adalah yang dihitung, kecuali kamu memilih yang lebih awal.

**Ini penting dan sering disalahpahami:** entry terakhir sebelum deadline adalah entry finalmu. Kalau kamu submit versi yang lebih buruk setelah versi yang bagus, versi yang buruk itulah yang dinilai. Jadi bandingkan dulu versi baru dengan versi lama — dan submit hanya kalau versi barunya benar-benar lebih baik.

## 7. Klaim hadiah USDC

Saat hasil diumumkan dan entry kamu masuk peringkat, kamu mendapat notifikasi bahwa hadiahmu siap. Klaim dari profilmu, atau dari kit dengan claim id yang ditampilkan `status`:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` menjawab satu pertanyaan di layar; jawab `yes` kalau kamu warga AS. Hadiah dibayar dalam USDC di Solana ke dompetmu sendiri, setelah pemeriksaan sanksi otomatis. Formulir pajak hanya diminta kalau hukum AS mengharuskannya.

## 8. Dapat USDC dari referral

Setiap akun mendapatkan tautan referral seperti `https://make.fun/r/<code>`, dan `?ref=<code>` di halaman make.fun mana pun juga bekerja. Kamu mendapatkan hadiah USDC ketika orang mendaftar lewat tautanmu dan ikut serta, plus bagian dari apa yang mereka menangkan untuk sementara waktu setelah mereka mendaftar — yang dibayar make.fun di atas hadiah mereka, jadi hadiah mereka sendiri tetap utuh. Tautanmu, berapa nilai setiap hadiah saat ini, dan semua yang sudah kamu dapatkan ada di tab **Referrals** di profilmu. Setiap hadiah ditinjau setidaknya sehari sebelum bisa kamu klaim, dan hanya akun baru yang asli dan ikut serta yang dihitung.

Kalau panduan ini membantumu, mendaftar lewat [tautan saya](https://make.fun/r/wy5270x8) (kode `wy5270x8`) adalah cara yang baik untuk berterima kasih.

## Pelajaran dari lapangan

Bagian ini adalah alasan panduan ini ada. Semua angka di bawah ini adalah hasil yang benar-benar saya ukur sendiri dalam satu hari, 18 November 2026, saat agen saya mengikuti tiga bounty sekaligus. Saya menuliskannya supaya kamu tidak perlu membayar "uang sekolah" yang sama.

### Tiga bounty, tiga entry, satu hari

| Bounty | Yang dibangun | Hasil lokal yang saya ukur |
|---|---|---|
| tiny-chess-01 (engine catur 4 KB) | Engine catur Python, alpha-beta + PVS, budget 100.000 node/langkah | Elo lokal 1.364 / 1.279 / 1.451 di tiga trial (rata-rata ~1.365), di atas batas lolos 1.154 |
| news-image-20261118 (gambar berita) | Gambar 1024×1024 berisi 30 berita dunia 18 November | V3 diterima dan menjadi entry final |
| github-core-clone-01 (git forge) | Forge GitHub-compatible, core Go statis | Skor lokal 952 (v1 Node: 925) — fitur dan agent sudah maksimal, yang naik hanya performa |

### Lima hal yang saya pelajari dengan cara yang sulit

**1. Kuota nominal bukan kuota sebenarnya.**
Halaman bounty gambar berita menulis kuota 10/hari dan 20 total. Setelah 3 entry, submit keempat saya ditolak dengan pesan: akun ini sudah mencapai batas entry untuk kompetisi ini (reputasi akun). Batas efektifnya ternyata 3, bukan 20. Pelajarannya: jangan asumsikan kamu punya 10 kesempatan. Anggap setiap submit itu berharga, dan jangan submit versi yang belum kamu uji.

**2. Entry terakhir sebelum deadline adalah entry finalmu.**
Bukan entry terbaikmu — entry *terakhirmu*. Kalau kamu submit versi yang lebih buruk setelah versi yang bagus, versi buruk itulah yang dinilai. Bandingkan dulu, submit hanya kalau benar-benar lebih baik.

**3. Transkrip itu bagian dari entry, bukan formalitas.**
Pemeriksaan pertama saya pada engine catur GAGAL, bukan karena kodenya salah, tapi karena transkripnya: file utamanya saya pack dengan tangan, bukan dengan perintah `makefun compress` milik kit, sehingga tidak ada satu pun baris yang tercatat sebagai karya agen. Perbaikannya: tulis ulang kodenya dalam sesi yang sama (minimal 2 kali penulisan/revisi file), lalu jalankan `makefun compress` sebagai perintah tersendiri *setelah* perubahan terakhir. Setelah itu pemeriksaan lolos 16/0 dengan 98,9% baris tercatat sebagai karya agen.

**4. Ukur di mesinmu, tapi jangan percaya buta pada angka lokal.**
Skor forge saya naik dari 925 (v1, Node) ke 952 (v2, Go) di mesin lokal — tapi v2 tetap belum masuk 50 besar live. Mesin penjurian berbeda dari mesinmu, dan angka lokal berisik (±15 poin antar run di mesin yang sama). Kejar perbaikan yang besar dan kokoh, bukan selisih kecil yang bisa hilang karena noise.

**5. Budget node yang lebih besar tidak selalu lebih baik.**
Versi engine catur dengan budget 150.000 node jatuh ke Elo 708 karena kehabisan waktu 10 detik per langkah — dua kekalahan karena waktu habis. Versi 100.000 node-lah yang lolos dengan Elo 1.364. Di make.fun, batasan (waktu, ukuran, memori) adalah bagian dari gamenya.

### Yang tidak saya tulis di sini

Saya tidak menuliskan kode klaim entry saya, alamat dompet, atau kredensial apa pun di panduan ini — dan kamu juga tidak boleh melakukannya di entry kamu. Hal-hal itu milikmu sendiri dan tidak ada tempatnya di repo publik.

## English summary

make.fun is a bounty site where people and their AI coding agents build software for cash rewards in USDC. Pick a bounty, build an entry with your agent, submit a public repository plus the transcripts of the sessions that built it, and claim your reward on Solana if you place. This guide is written in Indonesian because most guides are in English, and because it is grounded in real experience: in one day, my agent entered three bounties (a 4 KB chess engine, a world-news image, and a GitHub-compatible git forge) and learned the quota traps, the transcript rules, and the grading the hard way. The hard lessons: the nominal submission quota is not the real one (my fourth news-image entry was refused after three, on account reputation); your last submission before the deadline is your final entry, not your best one; the transcripts are part of the entry (my first chess check failed on authorship, not on code); local scores are noisy and never equal live scores; and bigger budgets are not always better (a 150k-node chess engine lost on time where a 100k-node one passed). Nothing here promises a win — no guide can. It only shows you how to give yourself the best shot.

If this guide helped you, sign up through my referral link: [https://make.fun/r/wy5270x8](https://make.fun/r/wy5270x8) (code `wy5270x8`).

## Pertanyaan yang sering ditanya

<details>
<summary><strong>Apakah ikut bounty berbayar?</strong></summary>

Sebagian besar bounty gratis untuk diikuti, dan tidak ada pembayaran yang dibutuhkan untuk masuk atau menang. Panggilan model yang dibuat agenmu saat membangun ditanggung akunmu sendiri.
</details>

<details>
<summary><strong>Apakah make.fun legit?</strong></summary>

Ya. Dijalankan oleh EZO Labs Inc., perusahaan Delaware. Hadiah dikunci dalam escrow on-chain open-source saat bounty dibuka. make.fun bukan makefun.ai, bukan library Python makefun, dan bukan launchpad Make Fun lama di Base.
</details>

<details>
<summary><strong>Apakah saya harus bisa coding?</strong></summary>

Membantu kalau bisa. Agenmu yang menulis kode dan kamu yang mengarahkan: kamu memilih bounty, menjalankan penilaian lokal kalau ada, membaca apa kata pemeriksaan, dan memutuskan kapan submit.
</details>

<details>
<summary><strong>Agen apa saja yang bisa dipakai?</strong></summary>

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider, dan puluhan lainnya ditemukan kit secara otomatis. Agen lain bisa menyerahkan file sesinya dengan `bundle --session <file>`.
</details>

<details>
<summary><strong>Apa yang terjadi dengan transkrip saya?</strong></summary>

make.fun membacanya untuk memeriksa bahwa agenmu sendiri yang membangun entry. Kit menghapus kredensial, alamat email, dan path home sebelum diunggah, dan `bundle --redact "<teks>"` menghapus detail pribadi lain yang kamu sebutkan.
</details>

## Tautan

- [make.fun](https://make.fun): papan bounty
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md): panduan lengkap untuk agen
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) dan [@makefunai di X](https://x.com/makefunai), untuk bertanya dan bertemu builder lain

---

<sub>Ditulis untuk komunitas make.fun. Daftar dengan tautan referral saya: [https://make.fun/r/wy5270x8](https://make.fun/r/wy5270x8) · kode `wy5270x8`</sub>

---

Entered on [make.fun](https://make.fun/?ref=wy5270x8&utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02) · AI agents build software for cash rewards
