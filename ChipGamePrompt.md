# Daftar Ide

| Nama Game | Konsep | Mekanisme |
| --- | --- | --- |
| **Data Rescue: Cyber Labyrinth** | Program antivirus kecil mengumpulkan kepingan data terkorupsi di papan sirkuit. | Menghindari *bug* atau *firewall* musuh, mengumpulkan kunci digital, dan membuka pintu keamanan warna-warni sebelum waktu habis. |
| **Alchemist's Grid** | Alkemis melintasi ubin-ubin elemen untuk mencapai portal keluar. | Memanfaatkan interaksi ubin elemen (es mencair oleh api, air memadamkan rintangan, dan tanah membuat jembatan sementara). |
| **Warehouse Circuit** | Perpaduan *Sokoban* klasik dengan labirin berwaktu berbasis *grid*. | Menggeser kotak baterai ke titik *docking*, sambil melepaskan rintangan, dan menghindari laser aktif. |
| **Time-Tinker** | Perbaikan mesin waktu dengan menyambungkan kembali sirkuit energi. | Menggeser ubin pipa atau roda gigi agar aliran energi mencapai generator utama dalam batas langkah. |
| **Dungeon Relics** | Eksplorasi *dungeon* retro untuk mencari relik kuno. | Mengumpulkan permata, menginjak sakelar lantai untuk dinding geser, dan menghindari musuh berpatroli. |
| **Space Janitor** | Robot pembersih merapikan kontainer limbah beracun di stasiun luar angkasa. | Menggeser kontainer ke lokasi pembuangan, menghindari laser berkala, dan mengitari tumpahan zat asam. |
| **Eco-Roots** | Menumbuhkan akar pohon atau aliran air melintasi ubin tanah kompleks. | Mencari jalur ke benih terkubur, menghindari batu karang, dan memanfaatkan tetesan air khusus. |
| **Cyber Heist** | Penyusupan spionase siber ke dalam *mainframe* brankas gedung. | Menghindari kamera pengawas, mematikan sistem keamanan lewat terminal pusat, dan kabur sebelum *firewall* aktif. |
| **Kitchen Panic** | Koki mengumpulkan bahan makanan di dapur restoran yang sibuk. | Menghindari pelayan bergerak, melintasi lantai licin, dan mengambil resep rahasia berpacu dengan waktu. |
| **Mystic Library** | Penjelajahan perpustakaan sihir tua untuk mengumpulkan lembaran mantra. | Memindahkan rak buku untuk membuka jalan, menggunakan ubin teleportasi, dan mengelabui hantu penjaga. |
| **Abyssal Diver** | Penyelam mengumpulkan mutiara langka di labirin terumbu karang dasar laut. | Memperhatikan meteran oksigen sebagai batas langkah, memanfaatkan arus air searah, dan membuka gerbang kerang dengan kunci mutiara. |
| **Museum Mayhem** | Penyusupan pencuri ke galeri museum untuk mengambil lukisan dan artefak berharga. | Menghindari pola sorotan kamera pengawas, melewati ubin sensor tekanan, dan keluar lewat pintu darurat. |


# ROLE & KONTEKS
Bertindaklah sebagai Senior Game Designer dan Software Architect spesialis game 2D berbasis grid (tile-based). Saya sedang merencanakan pengembangan game teka-teki 2D menggunakan Lazarus IDE / Free Pascal (FPC) yang terinspirasi dari mekanik game klasik "Chip's Challenge".

# TUJUAN
Saya butuh Game Design Document (GDD) teknis dan naratif yang mendeskripsikan secara menyeluruh gameplay loop, interaksi mekanik, dan rancangan logika sistem untuk game berikut:

* Nama/Tema Game: [**Isi nama atau konsep yang dipilih, contoh: "Data Rescue: Cyber Labyrinth"**]
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
