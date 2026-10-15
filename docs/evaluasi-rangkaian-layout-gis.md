# Evaluasi rangkaian pembuatan layout GIS

Evaluasi ini merangkum proses peta Jawa Barat dan DAS Citarum sebagai pengalaman proyek. Prinsip yang dapat dipakai ulang dituangkan dalam skill `gis-map-layout`; nama wilayah, instansi, warna, ukuran halaman, dan angka skala di bawah ini bukan aturan umum.

| Tahap | Temuan dari rangkaian pekerjaan | Perbaikan metode |
| --- | --- | --- |
| Layout awal | Susunan halaman sempat meniru template tanpa memuat QPT asli. Hasil dapat tampak serupa, tetapi item tidak mempertahankan asal dan struktur template yang diminta. | Muat QPT langsung, inspeksi itemnya, lalu adaptasi; buktikan QPT hasil dapat dibuka lagi. |
| Identitas dan teks | Logo, nama instansi, judul, dan item lama perlu diganti. Ekspor offscreen pada lingkungan ini menimbulkan masalah tampilan teks sehingga sempat dipakai gambar teks. | Pertahankan label QGIS yang dapat diedit dan uji render pada proses QGIS dengan GUI aktif bila ekspor headless bermasalah. |
| Warna dan simbol | Sebagian warna mempunyai padanan regulasi, sementara sebagian kelas RBI hanya memakai adaptasi warna. Menyamakan keduanya akan memberi kesan kepatuhan yang tidak didukung. | Periksa ruang lingkup aturan terhadap jenis data dan kelasnya; dokumentasikan padanan atau adaptasi, serta simpan style QML. |
| Peta dan legenda | Peta memerlukan kelas yang benar-benar tampil, simbol sungai terpilih, dan status area yang tidak terklasifikasi atau tidak tercakup. | Bandingkan legenda dengan renderer, layer aktif, dan status data; pisahkan isu geometri/data dari isu layout. |
| Revisi dari pengguna | QGZ yang telah diedit pengguna memuat perubahan visual yang tidak boleh hilang saat ekspor ulang. | Jadikan proyek tersimpan terbaru sebagai acuan visual, bandingkan item QGZ/QPT dan PNG, lalu keluarkan revisi pada folder baru. |
| Sumber dan CRS | Nama berkas lokal pernah muncul sebagai sumber; metadata batas DAS tidak mengidentifikasi penerbit. Setelah pengguna menyebut BIG, atribusi diperbaiki. Teks koordinat yang diletakkan terlalu kecil di bawah skala sulit dibaca. | Tanyakan asal data yang belum terbukti; pisahkan sumber data dari metadata peta. Ambil CRS dari peta dan sediakan ruang yang memadai di panel skala. |
| Skala dan panel | Skala 20 km tidak memanfaatkan ruang sesuai preferensi pengguna. Penambahan tiga baris CRS menuntut penyesuaian kotak skala, inset, dan legenda sebagai satu susunan. | Tentukan panjang skala dari extent dan lebar kotak, lalu ubah batas panel dan semua isinya secara konsisten; periksa hasil cetak. |
| Validasi akhir | Kode dapat memeriksa path, layer, template, ukuran A4, DPI, dan label yang ada, tetapi tidak cukup untuk menilai keterbacaan. | Buka ulang QGZ/QPT dan tinjau PNG penuh serta bagian padat pada resolusi aslinya. |

Pelajaran lintas proyek: mulai dari bukti data dan artefak terbaru; gunakan template sungguhan bila diminta; rancang panel sebagai sistem ruang; buat teks sumber tepat dan ringkas; validasi secara programatik sekaligus visual; simpan hasil revisi tanpa menimpa sumber.
