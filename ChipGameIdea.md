# ROLE & KONTEKS
Bertindaklah sebagai Senior Game Designer dan Software Architect spesialis game 2D berbasis grid (tile-based). Saya sedang merencanakan pengembangan game teka-teki 2D menggunakan Lazarus IDE / Free Pascal (FPC) yang terinspirasi dari mekanik game klasik "Chip's Challenge".

# TUJUAN
Saya butuh Game Design Document (GDD) teknis dan naratif yang mendeskripsikan secara menyeluruh gameplay loop, interaksi mekanik, dan rancangan logika sistem untuk game berikut:

* Nama/Tema Game: [Isi nama atau konsep yang dipilih, contoh: "Data Rescue: Cyber Labyrinth"]
* Genre: Tile-based Grid Puzzle Game
* Target Framework/Platform: Lazarus FPC (Render grafis berbasis 2D Grid / TCanvas / BGRAControls)

# DETAIL YANG HARUS DIJELASKAN
Jelaskan konsep game tersebut secara komprehensif ke dalam poin-poin terstruktur berikut:

1. Core Gameplay Loop:
   * Penjelasan siklus permainan utama dari awal level hingga akhir level.
   * Tujuan utama pemain di setiap ronde.

2. Grid Mechanics & Aturan Spasial:
   * Ukuran standar grid (misal: 16x16 / 32x32 tile) dan orientasi koordinat.
   * Cara pergerakan karakter (langkah per-tile, sistem turn/tick, atau real-time berwaktu).

3. Katalog Objek & Tile Interaktif:
   * Player Character: State, atribut, dan batasan gerakan.
   * Collectibles: Barang yang harus dikumpulkan untuk menyelesaikan stage.
   * Kunci & Pintu/Gerbang: Sistem warna/kategori kunci dan interaksinya.
   * Hazard / Jebakan: Jenis rintangan statis maupun dinamis (misal: laser berwaktu, lantai licin, lubang).
   * Blok/Beban Bergerak: Mekanik dorong/tarik objek di atas grid (jika ada).
   * Musuh / Patrol Entity: Pola pergerakan AI musuh (jika ada).

4. Kondisi Menang, Kalah, & Batasan (Constraints):
   * Win Condition (Kondisi lolos ke level berikutnya).
   * Lose Condition (Kematian karakter, kehabisan waktu/langkah).
   * Sistem Skor / Evaluasi performa pemain.

5. Panduan Logika Pemrograman (Data Structure Preview):
   * Pemetaan konsep objek ke dalam representasi Array 2D (contoh kode ID tile: 0=Kosong, 1=Dinding, 2=Kunci Merah, dst.).
   * Event loop atau State Machine sederhana yang dibutuhkan (Input -> Validasi Gerak -> Cek Interaksi Tile -> Update Grid -> Render).

# FORMAT OUTPUT
Sajikan jawaban dalam format Markdown yang rapi, scannable, hindari penjelasan yang terlalu abstrak/puitis, dan prioritaskan kejelasan aturan logika (rule-set) yang siap diterjemahkan ke dalam kode Pascal.
