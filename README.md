# RasyadevLHC

**Hardcore gameplay, PvP balancing, social roleplay, dan randomized trading shop untuk Minecraft Paper.**

RasyadevLHC menghadirkan kumpulan sistem gameplay untuk server Hardcore: pembatasan item PvP, cooldown Ender Pearl dan Trident, interaksi geledah/sekap berbasis persetujuan, serta shop event dengan GUI trading villager yang dapat dikelola langsung oleh admin.

> **Versi:** 1.1.0  
> **Platform:** Minecraft Java Edition — Paper 26.3  
> **Java:** Java 25  
> **Dokumentasi:** Repository ini berisi panduan penggunaan. File plugin `.jar` disediakan melalui kanal distribusi/pembelian, bukan melalui source code di repository ini.

---

## Daftar Isi

- [Fitur](#fitur)
- [Persyaratan](#persyaratan)
- [Instalasi](#instalasi)
- [Perintah Pemain](#perintah-pemain)
- [Perintah Admin](#perintah-admin)
- [Mengelola Shop](#mengelola-shop)
- [Konfigurasi](#konfigurasi)
- [Permission](#permission)
- [Catatan Penting](#catatan-penting)
- [Troubleshooting](#troubleshooting)
- [Pembelian dan Dukungan](#pembelian-dan-dukungan)

## Fitur

### Gameplay dan balance

- **Phantom disabled** — Phantom tidak dapat spawn.
- **Totem drop disabled** — Totem of Undying dari Evoker dinonaktifkan agar sumber Totem dapat dikendalikan melalui sistem shop.
- **Player tracker disabled** — penggunaan klik kanan Compass dapat dinonaktifkan.
- **Koordinat debug dibatasi** — mengaktifkan reduced debug info dari sisi server untuk client vanilla.
- **Elytra disabled** — pemain tidak dapat melakukan gliding menggunakan Elytra.
- **Mending fishing** — peluang custom mendapatkan Mending melalui fishing dapat diatur; sumber Mending vanilla lain dibatasi oleh plugin.
- **Tipped arrow disabled** — efek potion dari tipped arrow tidak diterapkan.
- **Chat toggle** — chat server dapat diaktifkan atau dinonaktifkan melalui konfigurasi.

### PvP balancing

- **Limit End Crystal + Respawn Anchor** — jumlah gabungan item di inventory dibatasi, default **30 item**.
- **Cooldown Ender Pearl** — default **15 detik**, dengan countdown di action bar.
- **Cooldown Trident** — default **15 detik**, termasuk pengecekan penggunaan Trident dan Riptide, dengan countdown di action bar.
- Pesan cooldown tidak memenuhi chat; sisa waktu ditampilkan lewat action bar.

### Social roleplay

- **Geledah inventory** — pemain mengirim permintaan dan target harus menerima sebelum inventory dapat dilihat. View bersifat read-only.
- **Capture / sekap RP** — permintaan harus diterima target. Target dibawa oleh pemain yang melakukan capture dan dapat dilepaskan dengan Shift oleh pembawa.
- Permintaan geledah/capture kedaluwarsa setelah **30 detik**.
- Pesan geledah, capture, dan sekap mengikuti teks yang disediakan dalam konfigurasi plugin.

### Randomized shop

- Shop terbuka secara acak setiap hari pada rentang **12.00 WIB–01.00 WIB** keesokan harinya.
- Durasi default event: **15 menit**.
- Bossbar menampilkan status dan countdown event.
- Shop menggunakan GUI trading villager.
- Satu shop mendukung hingga **10 trade**. Setiap trade dapat memiliki Input 1, Input 2 opsional, hasil, dan batas penggunaan sendiri.
- Netherite Ingot dapat dipakai sebagai mata uang trade dan dicegah masuk ke container biasa.
- Admin dapat membuka atau menghentikan event secara manual tanpa menunggu jadwal random.

## Persyaratan

- Minecraft Java Edition dengan **Paper 26.3**.
- **Java 25** untuk menjalankan server Paper 26.3.
- Akses untuk menaruh file plugin ke direktori `plugins/` dan me-restart server.

Paper/Spigot versi lain tidak dijamin kompatibel. Penggunaan bersama plugin economy, anti-cheat, custom tracker, atau plugin trading lain bisa memerlukan penyesuaian.

## Instalasi

1. Pastikan server menggunakan Paper 26.3 dan Java 25.
2. Unduh file `RasyadevLHC-1.1.0.jar` dari kanal distribusi resmi yang diberikan saat pembelian.
3. Matikan server sebelum mengganti versi plugin.
4. Letakkan file `.jar` ke folder `plugins/`.
5. Jalankan server. Plugin akan membuat folder konfigurasi `plugins/RasyadevLHC/`.
6. Buka `config.yml` untuk menyesuaikan fitur, peluang Mending, limit PvP, cooldown, dan jadwal shop.
7. Jalankan `/lhc reload` setelah mengubah konfigurasi yang didukung, atau restart server jika perubahan tidak diterapkan.
8. Uji terlebih dahulu pada server staging/test sebelum memasang di server utama.

**Penting:** backup folder `plugins/RasyadevLHC/`, termasuk `config.yml`, `shops.yml`, dan `schedule.yml`, sebelum melakukan update.

## Perintah Pemain

| Perintah | Fungsi |
|---|---|
| `/shop` | Membuka satu-satunya shop jika hanya ada satu; jika ada beberapa shop, menampilkan daftar nama shop. Event harus aktif atau pemain memiliki permission bypass. |
| `/shop <nama_shop>` | Membuka shop tertentu jika event sedang aktif. |
| `/geledah <player>` | Mengirim permintaan untuk melihat inventory pemain. |
| `/geledahaccept` | Menerima permintaan geledah. |
| `/geledahdeny` | Menolak permintaan geledah. |
| `/capture <player>` | Mengirim permintaan capture/sekap RP. |
| `/captureaccept` | Menerima permintaan capture. |
| `/capturedeny` | Menolak permintaan capture. |

Interaksi cepat yang didukung:

- **Geledah:** Shift dua kali lalu klik kanan target.
- **Capture:** Shift + klik kanan target.

Target harus menerima permintaan sebelum tindakan dimulai. Permintaan akan kedaluwarsa setelah 30 detik.

## Perintah Admin

Perintah admin memerlukan permission `rasyadev.admin`, kecuali bila disebutkan berbeda.

| Perintah | Fungsi |
|---|---|
| `/lhc help` | Menampilkan bantuan plugin. |
| `/lhc status` | Melihat status event dan jumlah shop. |
| `/lhc reload` | Memuat ulang konfigurasi dan jadwal. |
| `/lhc shop create <nama>` | Membuat shop dan membuka editor. |
| `/lhc shop edit <nama>` | Mengedit shop yang sudah ada. |
| `/lhc shop delete <nama>` | Menghapus shop beserta semua trade di dalamnya. |
| `/lhc shop uses <nama> <max>` | Mengatur batas penggunaan untuk trade dalam shop; `0` berarti unlimited. Perubahan ini mereset pemakaian. |
| `/lhc shop list` | Menampilkan daftar shop. |
| `/lhc shop start <durasi>` | Memulai event shop secara manual. |
| `/lhc shop stop` | Menghentikan event shop aktif. |
| `/shopadmin create <nama>` | Alias perintah untuk membuat shop. |
| `/shopadmin edit <nama>` | Alias perintah untuk mengedit shop. |
| `/shopadmin delete <nama>` | Alias perintah untuk menghapus shop. |
| `/shopadmin list` | Menampilkan daftar shop. |

Contoh durasi manual:

- `/lhc shop start 15` — 15 menit.
- `/lhc shop start 30m` — 30 menit.
- `/lhc shop start 1h30m` — 1 jam 30 menit.

Angka tanpa satuan berarti menit. Durasi event manual maksimal tujuh hari.

## Mengelola Shop

1. Buat shop, misalnya `/lhc shop create lapershop`.
2. Di GUI admin, masukkan item langsung ke slot input. Item dapat dipindahkan dengan klik atau drag dari inventory.
3. Lengkapi **Input 1** dan **Result**. **Input 2** boleh dikosongkan.
4. Gunakan kontrol tambah/hapus dan navigasi untuk mengatur hingga 10 trade dalam satu shop.
5. Atur `Max Uses` untuk membatasi jumlah transaksi per trade. Pilih unlimited bila stok tidak perlu dibatasi.
6. Tekan tombol simpan pada GUI agar perubahan diterapkan.
7. Pemain dapat mengaksesnya menggunakan `/shop lapershop` saat event dibuka.

### Slot GUI editor

| Slot | Fungsi |
|---:|---|
| 11 | Input 1 |
| 13 | Input 2 (opsional) |
| 15 | Result / item hasil |
| 18 / 19 | Trade sebelumnya / berikutnya |
| 20 | Menambahkan trade |
| 21 | Menghapus trade yang sedang dipilih |
| 22 | Mengatur `Max Uses` trade yang sedang dipilih |
| 24 | Menghapus seluruh shop |
| 26 | Menyimpan perubahan shop |

Trade disimpan dalam `plugins/RasyadevLHC/shops.yml`. Jadwal random disimpan di `plugins/RasyadevLHC/schedule.yml`.

Pada instalasi pertama, plugin dapat membuat contoh shop `totem` dengan trade **8 Netherite Ingot → 1 Totem of Undying** jika opsi contoh shop masih diaktifkan.

## Konfigurasi

File utama: `plugins/RasyadevLHC/config.yml`.

| Pengaturan | Default | Keterangan |
|---|---:|---|
| `features.phantom-disabled` | `true` | Menonaktifkan spawn Phantom. |
| `features.totem-evoker-drops-disabled` | `true` | Menonaktifkan drop Totem dari Evoker. |
| `features.player-tracker-disabled` | `true` | Membatasi penggunaan klik kanan Compass. |
| `features.coordinates-hidden` | `true` | Mengaktifkan reduced debug info untuk client vanilla. |
| `features.elytra-disabled` | `true` | Menonaktifkan Elytra gliding. |
| `features.mending-fishing-only` | `true` | Mengaktifkan pembatasan sumber Mending. |
| `mending.fishing-chance` | `0.0025` | Peluang custom Mending sebesar **0,25%**. |
| `pvp.crystal-anchor-limit` | `30` | Limit gabungan End Crystal + Respawn Anchor. |
| `pvp.pearl-cooldown-seconds` | `15` | Cooldown Ender Pearl dalam detik. |
| `pvp.trident-cooldown-seconds` | `15` | Cooldown Trident dalam detik. |
| `social.request-timeout-seconds` | `30` | Durasi valid permintaan social. |
| `shop.timezone` | `Asia/Jakarta` | Zona waktu jadwal shop. |
| `shop.window-start` | `12:00` | Mulai rentang event random. |
| `shop.window-end` | `01:00` | Akhir rentang event random pada hari berikutnya. |
| `shop.duration-minutes` | `15` | Durasi default event shop. |
| `shop.bossbar-enabled` | `true` | Mengaktifkan bossbar event. |

Pesan plugin dapat disesuaikan pada bagian `messages` menggunakan format MiniMessage. Hindari mengubah key pesan yang tidak dikenal.

## Permission

| Permission | Default | Keterangan |
|---|---|---|
| `rasyadev.command` | Semua pemain | Mengakses command utama `/rasyadev` dan alias `/lhc`. |
| `rasyadev.admin` | Operator | Mengelola shop, event, dan konfigurasi. |
| `rasyadev.shop.bypass` | Operator | Membuka shop ketika event random sedang tertutup. |

## Catatan Penting

- **Koordinat:** reduced debug info hanya membatasi informasi debug pada client vanilla yang mematuhi aturan server. Plugin tidak dapat menjamin koordinat tersembunyi dari client modded atau mod yang mengabaikan aturan tersebut.
- **Compass:** saat fitur tracker aktif, klik kanan Compass biasa juga ikut diblokir. Plugin tidak otomatis mengenali sistem tracker khusus dari plugin lain.
- **Totem:** konfigurasi saat ini menonaktifkan drop Totem dari Evoker secara umum, bukan hanya Evoker yang muncul dalam raid.
- **Mending:** chance `0.0025` sama dengan 0,25%. Periksa kompatibilitas jika server memakai plugin fishing, enchantment, atau loot tambahan.
- **Netherite Ingot:** ingot diperlakukan sebagai mata uang dan tidak dapat dimasukkan ke container biasa. Netherite Block tetap dapat ditempatkan sebagai blok.
- **Limit PvP:** limit 30 menghitung gabungan End Crystal dan Respawn Anchor di inventory; bukan batas jumlah yang sudah ditempatkan di dunia.
- **Multi-trade:** satu shop mendukung maksimal 10 trade. Gunakan klik normal untuk trade dengan stok terbatas; shift-click/double-click mungkin dibatasi untuk mencegah stok terlewati.

## Troubleshooting

**Plugin tidak muncul atau gagal dimuat**

- Pastikan server benar-benar menjalankan Paper 26.3 dan Java 25.
- Periksa `logs/latest.log` untuk pesan error saat startup.
- Pastikan hanya ada satu versi `RasyadevLHC` di folder `plugins/`.

**Shop tertutup saat ingin digunakan**

- Shop normal hanya tersedia selama event berlangsung.
- Admin dapat membuka event dengan `/lhc shop start 15`.
- Permission `rasyadev.shop.bypass` dapat digunakan untuk membuka shop di luar event.

**Trade tidak dapat dibeli**

- Periksa apakah `Input 1`, `Result`, dan—jika dipakai—`Input 2` sudah disetel benar.
- Periksa `Max Uses` atau stok trade.
- Untuk trade dengan stok terbatas, gunakan klik normal dan hindari shift-click/double-click.

**Perubahan konfigurasi belum diterapkan**

- Jalankan `/lhc reload` atau restart server.
- Periksa indentasi YAML dan pastikan value sesuai format yang digunakan.

## Pembelian dan Dukungan

RasyadevLHC didistribusikan sebagai plugin siap pakai. Repository ini berisi dokumentasi dan **tidak menyediakan source code**.

- **Harga:** `CHAT DI DISCORD`
- **Pembelian:** `DISCORD`
- **Dukungan:** `https://discord.gg/nMh2N9f7X`
- **Pembaruan dan ketentuan lisensi:** `RasyaDEV`

Sebelum membeli, pastikan server kamu memenuhi persyaratan versi. Sertakan versi Paper, versi Java, dan potongan error dari `logs/latest.log` ketika meminta bantuan teknis. Jangan mengirim seluruh folder server atau informasi rahasia.

---

<p align="center">
  <strong>RasyadevLHC</strong><br>
  Dibuat oleh Rasyadev · Hardcore gameplay tools for Paper
</p>
