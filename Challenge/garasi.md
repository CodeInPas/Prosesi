
**Judul Proyek:** GARASI — Aplikasi Manajemen Bengkel & Toko Sparepart
**Klien:** Pemilik "Bengkel Kawan" (1 lokasi aktif, cabang ke-2 dalam rencana 1 tahun ke depan)
**Jenis Aplikasi:** Desktop native, offline-first
**Durasi Kerja:** 8 minggu
**Status Dokumen:** Terbuka untuk penawaran

---

## 1. Latar Belakang

Saat ini operasional bengkel saya masih menggunakan buku tulis dan nota rangkap. Masalah utama: pencatatan stok sparepart kacau, riwayat servis pelanggan tidak tersimpan, keuntungan per servis tidak terukur, dan kasir sering salah hitung. Saya butuh **satu aplikasi desktop** yang menangani semuanya secara lokal — **tanpa ketergantungan internet** untuk fungsi inti, karena koneksi di lokasi tidak stabil.

---

## 2. Lingkup & Modul

### Modul Wajib

**A. Master Data**
- CRUD pelanggan + kendaraan (1 pelanggan bisa punya banyak kendaraan)
- CRUD item sparepart (kode, barcode, kategori, satuan, harga beli/jual, stok minimum)
- CRUD mekanik/teknisi + tarif jasa
- CRUD pemasok

**B. Work Order (WO) Servis**
- Pembuatan WO: pelanggan, kendaraan, keluhan, estimasi biaya
- Item WO: jasa + sparepart, status per item (antri → proses → selesai)
- Persetujuan estimasi oleh pelanggan (dicatat sebagai flag)
- Konversi WO → invoice dalam satu klik
- Papan status WO yang terlihat jelas (board sederhana)

**C. Kasir / Penjualan**
- Transaksi penjualan retail + penjualan part ke WO
- Scan barcode & pencarian item cepat (termasuk pencarian toleran salah ketik)
- Diskon per item / total, pembayaran tunai & non-tunai, kembalian
- Parkir transaksi (hold) & retur penjualan
- **Cetak struk printer thermal 58/80mm (ESC/POS) dan invoice A5**

**D. Stok & Pembelian**
- Stok masuk (pembelian pemasok), stok keluar otomatis dari WO/penjualan
- Stok opname & penyesuaian manual (dengan alasan, tercatat)
- Peringatan stok di bawah minimum di dashboard

**E. Laporan & Dashboard**
- Laporan: penjualan, laba kotor, produktivitas per mekanik, stok, umur stok
- Filter periode/kategori/pemasok; export PDF & CSV; cetak
- Dashboard: grafik pendapatan harian & top-10 sparepart terjual

**F. Pengguna & Keamanan**
- Role: admin, kasir, kepala bengkel, mekanik (mekanik hanya lihat WO miliknya)
- Audit trail: semua transaksi dan perubahan harga/stok tercatat (siapa, kapan, apa)

**G. Backup**
- Backup otomatis terjadwal + manual (terkompresi), restore dengan validasi integritas

### Modul Bonus (nilai tambah, tidak wajib)
1. Sinkronisasi data antar-cabang (push-pull via REST sederhana + penanganan konflik)
2. Auto-update aplikasi
3. Manajemen piutang pelanggan (kredit)

---

## 3. Kebutuhan Non-Fungsional

| No | Kriteria | Target |
|----|----------|--------|
| N1 | OS utama | Windows 10/11 x64 (Linux = nilai tambah) |
| N2 | Fungsi inti tanpa internet | 100% offline-first |
| N3 | Startup aplikasi | < 3 detik |
| N4 | Pencarian item | < 300 ms pada 50.000 SKU |
| N5 | Buka layar transaksi baru | < 500 ms |
| N6 | Cetak struk | muncul di printer < 2 detik, **UI tidak boleh not responding** |
| N7 | Password | di-hash, tidak boleh hardcoded di source |
| N8 | Crash/PC mati di tengah transaksi | data tetap konsisten saat restart (transaksi bersifat atomik) |
| N9 | RAM saat operasional 8 jam | stabil, < 500 MB |
| N10 | Log error ke file | untuk diagnosa jarak jauh |

---

## 4. Deliverables

1. **Source code lengkap** (repositori Git, dengan history yang rapi) + instruksi build dari nol di mesin bersih
2. **Installer** (satu file + uninstaller) dan binary siap pakai
3. **Skema database + ERD**
4. **Manual pengguna** (PDF) + video demo singkat per modul (max 10 menit total)
5. **Dokumen teknis ringkas**: arsitektur, alasan pemilihan teknologi, batasan yang diketahui
6. **Data dummy** untuk demo (min. 1.000 SKU, 100 pelanggan, 50 transaksi)
7. **Unit test minimal** untuk logika inti: perhitungan total & diskon, pengurangan stok, retur

---

## 5. Milestone & Pembayaran

| Milestone | Minggu | Cakupan | Pembayaran |
|-----------|--------|---------|-----------|
| M1 | 1–2 | Desain DB, prototipe UI, master data | — (review arah) |
| M2 | 3–4 | WO + kasir + cetak struk | 30% |
| M3 | 5–6 | Stok, laporan, dashboard, backup, role | 40% |
| M4 | 7 | Beta + perbaikan hasil UAT saya | — |
| M5 | 8 | Rilis final + seluruh deliverable | 30% |

Garansi perbaikan bug: **90 hari** setelah serah terima, tanpa biaya.

---

## 6. Kriteria Evaluasi Penawaran

| Aspek | Bobot |
|-------|-------|
| Kesesuaian fungsional (demo sesuai daftar FR) | 30 |
| Arsitektur & kualitas kode (struktur, penanganan error, keterbacaan) | 20 |
| Desain data (integritas, backup, skema masuk akal) | 15 |
| UI/UX — terutama kecepatan kerja kasir | 10 |
| Performa & stabilitas (uji skenario di bawah) | 10 |
| Deployment, installer, dokumentasi | 10 |
| Modul bonus | 5 |

---

## 7. Skenario Uji Penerimaan (contoh)

- **U1:** Import 10.000 SKU dari CSV < 60 detik; pencarian tetap responsif
- **U2:** Struk 50 item + diskon campuran, cetak ke printer thermal 80mm
- **U3:** Retur barang → stok bertambah kembali, audit trail tercatat
- **U4:** Backup → restore di PC lain → data identik
- **U5:** Login sebagai kasir → menu ubah harga & laporan laba tidak muncul
- **U6:** Aplikasi dimatii paksa (simulasi listrik padam) saat transaksi → tidak ada data setengah jadi
- **U7:** Print 50 struk berturut-turut → UI tetap responsif

---

## 8. Batasan Teknis (baca catatan saya)

> **Anda bebas memilih bahasa, framework, dan pustaka — apa pun — asalkan hasilnya aplikasi desktop native.** Yang saya nilai adalah hasil dan kualitasnya, bukan tool-nya.

Satu-satunya batasan mutlak: database harus **berjalan lokal/embedded** (tidak wajib server terpisah), karena saya hanya punya 1 PC kasir dan 1 PC admin di awal.

---

## 9. Yang Harus Ada di Penawaran Anda

1. Stack yang akan dipakai + **alasan singkat** pemilihannya
2. Estimasi per modul & jadwal terhadap milestone di atas
3. Harga penawaran (dengan rincian)
4. **Contoh kode nyata** milik Anda (potongan/modul lama yang sudah pernah dibuat) — ini yang paling saya lihat untuk menilai gaya koding Anda
5. Portofolio/ringkasan pengalaman (3–5 teratas saja)
6. **Jawaban 3 pertanyaan ini** (untuk mengukur cara berpikir Anda, jawaban 1 paragraf per pertanyaan):
   - a) Bagaimana Anda memastikan stok tetap konsisten jika dua transaksi terjadi nyaris bersamaan?
   - b) Bagaimana desain proses cetak struk agar UI tidak membeku saat printer lambat/mati kertas?
   - c) Jika 6 bulan lagi saya minta fitur sinkronisasi 2 cabang, bagaimana struktur data yang Anda rancang hari ini supaya itu tidak jadi mimpi buruk?
7. Pertanyaan klarifikasi dari Anda ke saya, jika ada

---

**Batas pengajuan penawaran: 7 hari sejak dokumen ini diterbitkan.**
Klarifikasi boleh kapan saja selama masa penawaran.

---

*Catatan internal (tidak memengaruhi penilaian): saya sudah sering melihat aplikasi desktop yang "jalan tapi rapuh" — crash saat printer mati, data hilang saat listrik padam. Fokus pengujian saya bukan pada banyaknya fitur, tapi pada ketahanan aplikasi di kondisi nyata yang tidak ideal.*

---

