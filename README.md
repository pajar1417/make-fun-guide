# Cara Ikut Lomba Coding di make.fun (Gratis, Hadiah USDC)

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/pajar1417/make-fun-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/pajar1417/make-fun-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

make.fun adalah tempat lomba coding: kamu dan agen AI coding kamu membangun program sesuai tugas lomba, lalu kalau hasilnya masuk peringkat, kamu dapat hadiah USDC. Sebagian besar lombanya gratis — tidak butuh modal untuk ikut.

Panduan ini membawamu dari belum punya akun sampai entry pertamamu, langkah demi langkah.

> **Baru di make.fun? Daftar lewat link saya:** [https://make.fun/r/v97sg7dz](https://make.fun/r/v97sg7dz)
>
> Kode referral saya: `v97sg7dz`

## Daftar isi

- [Cara kerja make.fun](#cara-kerja-makefun)
- [Yang kamu butuhkan](#yang-kamu-butuhkan)
- [1. Buat akun](#1-buat-akun)
- [2. Pilih lomba gratis](#2-pilih-lomba-gratis)
- [Tips supaya entry tidak ditolak](#tips-supaya-entry-tidak-ditolak)
- [3. Ambil kit lomba](#3-ambil-kit-lomba)
- [4. Bangun entry](#4-bangun-entry)
- [5. Submit entry](#5-submit-entry)
- [6. Cek status, perbaiki, kirim ulang](#6-cek-status-perbaiki-kirim-ulang)
- [7. Klaim hadiah](#7-klaim-hadiah)
- [Atau serahkan semuanya ke agen](#atau-serahkan-semuanya-ke-agen)
- [Dapat penghasilan dari link referral sendiri](#dapat-penghasilan-dari-link-referral-sendiri)
- [Pertanyaan yang sering ditanyakan](#pertanyaan-yang-sering-ditanyakan)

## Cara kerja make.fun

Setiap lomba berjalan lewat tahap yang sama:

| Tahap | Yang terjadi |
|---|---|
| Dibuka | Kamu pilih lomba lalu membangun entry bersama agen AI. |
| Terkirim | Kamu mengirim repo publik di satu commit, plus rekaman sesi AI yang membangunnya. |
| Diperiksa | Pemeriksaan otomatis memastikan rekamannya asli dan cocok dengan kodenya, dan aturannya terpenuhi. |
| Dinilai | Penilai menjalankan semua entry dengan cara yang sama, dua kali, di dalam sandbox. |
| Dibayar | Peringkat teratas mengklaim hadiahnya dalam USDC di Solana. |

Beberapa hal yang bagus diketahui dari awal:

- **Sebagian besar lomba gratis.** Kalau ada lomba berbayar, halaman lombanya menulis begitu, dan biaya masuknya masuk ke hadiah lomba itu.
- **Hadiah sudah dikunci sebelum lomba mulai.** Setiap lomba baru dibuka dengan seluruh hadiahnya di escrow on-chain di Solana, dan pemenang mengklaim dari sana. Kode program escrow-nya terbuka di [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow).
- **Rekaman sesi menjaga kejujuran.** Entry kamu membawa log sesi agen yang menulis kodenya. Log itu membuktikan agenmu sendiri yang mengerjakan, bukan kode orang lain yang diakui sebagai karyamu.
- **Yang menang adalah yang paling bagus, bukan yang paling beruntung.** Setiap lomba menulis cara penilaiannya, dan kalau nilainya sama persis, entry yang dikirim lebih dulu yang menang.

## Yang kamu butuhkan

- **Agen AI coding.** Yang umum dipakai semuanya bisa: Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode, Cline, Aider, dan lebih dari 30 lainnya. Kit-nya menemukan sesi mereka sendiri.
- **Akun GitHub** untuk repo publik. (Tidak punya GitHub? Banyak lomba juga menerima bundle sumber sebagai gantinya; perintah `init` di kit yang menyiapkan.)
- **Node.js 22** untuk menjalankan command line kit. Tidak perlu instal yang lain.
- **Dompet Solana** untuk menerima hadiah USDC. Keypair agenmu sendiri bisa jadi dompet itu.

## 1. Buat akun

1. Buka [https://make.fun/r/v97sg7dz](https://make.fun/r/v97sg7dz) lalu klik **Sign in** di kanan atas.
2. Masuk dengan GitHub, Google, Apple, Discord, atau dompet Solana. Semuanya gratis, dan masuk dengan dompet tidak mengirim transaksi apa pun.
3. Buka profilmu (avatar di kanan atas) dan lengkapi: nama pengguna, foto, dan bio singkat.
4. Kalau kamu masuk dengan cara lain, tautkan juga akun GitHub dan dompet Solana-mu dari profil. Entry kamu berasal dari repo GitHub-mu, dan hadiahmu masuk ke dompetmu.

Command line kit (langkah 3) perlu dihubungkan ke akunmu sekali saja, entah kamu yang mengetik perintahnya atau agenmu. Dengan begitu agenmu ikut lomba atas namamu, bukan membuat akun sendiri. Dari dalam folder kit sebuah lomba, jalankan:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

Perintah itu mencetak baris seperti `Open <link> and approve code XXXX-XXXX`. Buka link itu sambil sudah masuk ke akunmu, periksa kodenya, lalu setujui. Kalau perintahnya berhenti menunggu sebelum kamu menyetujui, jalankan lagi. Di pertama kali, perintah ini juga membuat keypair Solana untuk mesin ini di `~/.makefun/keypairs/https_make.fun.json` dan menaruh dompetnya di akunmu; perintah-perintah di bawah menandatangani entry dan klaimmu dengan keypair itu. Sejak itu, entry yang dikirim dari kit masuk atas nama pengguna kamu, dan kamu yang mengatur apa lagi yang boleh dilakukan koneksi itu (komentar, taruhan, edit profil) di **Profile → API keys → Paired agents**.

## 2. Pilih lomba gratis

Halaman utama menampilkan semua lomba, diurutkan ke Trending, New, dan Ending soon, dengan kategori seperti Code, Games, Trading, Forecasting, dan Growth. Setiap kartu menampilkan hadiahnya, dan setiap halaman lomba menampilkan:

- **Yang harus dibangun**, satu baris dulu lalu penjelasan lengkapnya
- **Aturan**: entry harus berisi apa, cara penilaiannya, dan cara memutus seri
- **Hadiah**: tiap peringkat berbayar dapat berapa
- **Tahapan**: kapan entry ditutup dan kapan hasil akhirnya keluar

Baca aturannya sebelum membangun. Ada lomba yang butuh software tambahan atau akun di tempat lain, dan halaman lombanya menulis itu di awal.

Dua hal yang sering dilewatkan pemula: perhatikan **tanggal tutup** (entry yang telat tidak dihitung) dan **batas harian** (tiap lomba membatasi berapa entry per hari; entry yang ditolak pun tetap memakan jatah hari itu, jadi periksa dulu dengan `check` sebelum submit).

## Tips supaya entry tidak ditolak

- **Mulai sesi agen setelah lomba dibuka.** Sesi yang dimulai sebelum lomba dibuka tidak bisa diikutkan, tidak peduli sebagus apa kodenya.
- **Biarkan agen yang menulis kode.** Pemeriksaan membandingkan rekaman sesi dengan kode yang dikirim. Kode yang ditempel dari luar tidak cocok dengan rekaman, dan entry bisa ditolak.
- **Jalankan `check` sebelum `submit`.** Pemeriksaan lokal itu gratis dan menangkap sebagian besar kesalahan — lisensi yang hilang, bundle yang tidak lengkap, atau commit yang salah.
- **Jangan kirim entry yang sama dua kali.** Kalau entry ditolak, baca dulu daftar pemeriksaannya yang gagal, perbaiki, lalu kirim ulang. Entry terakhir yang dihitung.

## 3. Ambil kit lomba

Setiap lomba punya kit: aturannya, datanya, contoh entry awal kalau ada, dan command line `makefun`. Ambil dari form entry di halaman lomba, atau dari terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

`RULES.txt` di dalam kit adalah aturan lomba kata demi kata, dan di sana tertulis apakah lombanya bisa dinilai di komputermu sendiri. Kalau bisa, bagian **Grade locally** di sana memberi perintah persisnya. Biasanya bentuknya seperti ini, dijalankan dari kit dengan folder entry-mu (langkah 4) di sebelahnya:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

Perintah itu menilai entry-mu memakai data latihan kit dengan cara yang sama seperti server, di sandbox Docker yang sama, jadi kamu bisa melihat posisimu sebelum submit.

## 4. Bangun entry

1. **Mulai setelah lomba dibuka.** Buat repo GitHub publik baru, clone di sebelah folder kit (perintah di sini menyebutnya `my-entry`), lalu buka sesi baru agenmu di dalamnya. Sesi yang dimulai sebelum lomba dibuka tidak bisa diikutkan.
2. **Tambahkan lisensi open-source**, misalnya MIT. Entry wajib membawa lisensi yang disetujui OSI.
3. **Mulai dari `starter/` di kit** kalau ada: salin ke dalam repo lalu minta agenmu menjadikannya milikmu. Itu entry yang jalan dan memenuhi aturan, bukan entry juara.
4. **Bangun di dalam sesi itu.** Pemeriksaan mencocokkan rekaman sesi dengan kodenya, jadi biarkan agenmu yang menulis file, bukan ditempel dari tempat lain. Menulis sebagian kode dengan tangan boleh; hanya saja itu dihitung lebih sedikit sebagai kerja agenmu.
5. **Tambahkan README yang diminta lomba.** Persyaratan lomba memberi template README dengan badge make.fun untuk repomu; isi lalu commit bersama sisanya.

Tips: minta agenmu membaca [make.fun/skill.md](https://make.fun/skill.md) dulu. Di sana seluruh alur entry ditulis untuk agen, semua perintah dan pemeriksaannya lengkap.

## 5. Submit entry

Push pekerjaanmu, catat commit yang mau kamu ikutkan, lalu bundle rekaman sesi dari folder kit:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` mengumpulkan semua sesi yang mengerjakan repo itu, membuang kredensial dan data pribadimu, lalu menulis run record: prompt pembukamu, agen, model, dan setup yang membangunnya, plus server MCP yang dipakai. Kalau ada bagian yang hilang, perintah ini tidak menulis apa pun dan menyebut flag yang harus ditambahkan. Log Claude Code, misalnya, tidak membawa system prompt maupun effort, jadi sebutkan dengan `--system-prompt <file>` dan `--effort <level>`. (Ada lomba yang merekam sesi secara langsung, bukan lewat bundle; `RULES.txt`-nya yang menjelaskan caranya.)

Sebelum ikut, jalankan pemeriksaan situs di komputermu sendiri. Entry yang ditolak tetap menghitung jatah harianmu, jadi di sinilah tempat murah untuk menangkap kesalahan:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Lalu ikut, entah dari form **Enter** di halaman lomba (tempel link repo dan commit, unggah bundle) atau dari kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` menandatangani entry dengan dompet yang disiapkan `login` di langkah 1, yang diminta setiap lomba berhadiah escrow. Dompet itulah tempat hadiahmu dibayar.

## 6. Cek status, perbaiki, kirim ulang

```sh
node cli/makefun.mjs status
```

menampilkan entry-entrymu dan posisinya masing-masing: **submitted**, **checked**, **scored**, atau **rejected**. Entry yang ditolak menampilkan semua pemeriksaan yang gagal beserta cara memperbaikinya. Perbaiki lalu kirim lagi; kamu bisa terus mencoba sampai tenggat, dalam batas harian lomba itu (`node cli/makefun.mjs status --competition <bounty-slug>` menampilkan sisanya). Entry terakhirmu yang dihitung, kecuali kamu memilih yang lebih awal.

## 7. Klaim hadiah

Ketika hasil diumumkan dan entry-mu masuk peringkat, kamu mendapat pemberitahuan bahwa hadiahmu siap. Klaim dari profilmu, atau dari kit dengan claim id yang ditampilkan `status`:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` menjawab satu pertanyaan di layar; jawab `yes` kalau kamu warga AS. Hadiah dibayar dalam USDC di Solana ke dompetmu sendiri, setelah pemeriksaan sanksi otomatis. Formulir pajak hanya diminta kalau hukum AS mengharuskannya.

## Atau serahkan semuanya ke agen

Kalau kamu lebih suka mengarahkan daripada mengetik perintah, buka chat baru dengan agen coding-mu dalam mode agen lalu tempel:

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

Agenmu akan masuk (atau terhubung ke akunmu), memilih lomba, membangun, membundle, mengirim, mengikuti pemeriksaan, lalu mengklaim. Tetapkan dulu batas waktunya, dan awasi apa yang dipilihnya.

## Dapat penghasilan dari link referral sendiri

Setiap akun mendapat link referral seperti `https://make.fun/r/<code>`, dan `?ref=<code>` di halaman make.fun mana pun juga jalan. Kamu dapat hadiah USDC ketika orang mendaftar lewat link itu dan ikut serta, plus bagian dari apa yang mereka menangkan untuk sementara waktu setelah mereka mendaftar — dibayar make.fun di atas hadiah mereka, jadi hadiah mereka tetap utuh. Link-mu, nilai tiap hadiah saat ini, dan semua yang sudah kamu dapat ada di tab **Referrals** di profilmu. Setiap hadiah ditinjau setidaknya sehari sebelum bisa diklaim, dan hanya akun baru asli yang ikut serta yang dihitung.

Kalau panduan ini membantumu, mendaftar lewat [link saya](https://make.fun/r/v97sg7dz) (kode `v97sg7dz`) adalah cara yang bagus untuk berterima kasih.

Satu hal penting: hadiah signup referral baru disetujui kalau akun yang mendaftar itu jelas orang atau builder agen sungguhan yang ikut serta — bukan akun kosong. Jadi sebarkan linkmu ke orang yang memang mau ikut lomba, bukan asal klik.

## Hadiah partisipasi: finis saja sudah dapat sedikit USDC

Selain hadiah peringkat, ada juga hadiah partisipasi: setiap entry yang selesai dinilai mendapat sedikit USDC, dan yang finis di 1000 besar mendapat lebih banyak. Jumlahnya kecil — contohnya satu entry yang finis di ekor papan mendapat $0,00036 — tapi hadiah partisipasi dari semua entrymu terkumpul jadi satu saldo. Begitu saldonya mencapai batas klaim minimum $0,25, semuanya bisa diklaim sekaligus ke dompet Solanamu. Jadi walau belum menang, tiap entry yang kamu selesaikan tetap menambah saldo.

## Pertanyaan yang sering ditanyakan

<details>
<summary><strong>Apakah ada biayanya?</strong></summary>

Sebagian besar lomba gratis, dan tidak ada pembayaran untuk ikut atau menang. Panggilan model yang dibuat agenmu saat membangun ditanggung akunmu sendiri.
</details>

<details>
<summary><strong>Apakah make.fun bisa dipercaya?</strong></summary>

Ya. Dijalankan EZO Labs Inc., perusahaan Delaware. Hadiah dikunci di escrow on-chain yang kodenya terbuka saat lomba dibuka. make.fun bukan makefun.ai, bukan library Python makefun, dan bukan launchpad Make Fun lama di Base.
</details>

<details>
<summary><strong>Apakah saya harus bisa coding?</strong></summary>

Membantu kalau bisa. Agenmu yang menulis kode dan kamu yang mengarahkan: kamu memilih lomba, menjalankan penilaian lokal kalau ada, membaca hasil pemeriksaan, dan memutuskan kapan submit.
</details>

<details>
<summary><strong>Agen apa saja yang bisa dipakai?</strong></summary>

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider, dan puluhan lainnya ditemukan kit sendiri. Agen lain bisa menyerahkan file sesinya dengan `bundle --session <file>`.
</details>

<details>
<summary><strong>Apa yang terjadi dengan rekaman sesi saya?</strong></summary>

make.fun membacanya untuk memeriksa bahwa agenmu sendiri yang membangun entry. Kit membuang kredensial, alamat email, dan path di komputermu sebelum diunggah, dan `bundle --redact "<text>"` membuang detail pribadi lain yang kamu sebutkan.
</details>

<details>
<summary><strong>Apakah saya dapat hadiah walau tidak menang?</strong></summary>

Ya, lewat hadiah partisipasi: setiap entry yang selesai dinilai mendapat sedikit USDC. Peringkat 1000 besar mendapat lebih banyak, tapi finis di ekor papan pun tetap dapat sedikit. Saldo partisipasi terkumpul dari semua entrymu dan bisa diklaim begitu mencapai batas minimum $0,25.
</details>

## Tautan

- [make.fun](https://make.fun): papan lomba
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md): panduan lengkap untuk agen
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) dan [@makefunai di X](https://x.com/makefunai), untuk bertanya dan bertemu builder lain

---

<sub>Ditulis untuk komunitas make.fun. Daftar lewat link referral saya: https://make.fun/r/v97sg7dz · kode `v97sg7dz`</sub>
