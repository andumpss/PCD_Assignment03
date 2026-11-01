# Segmentasi Citra dan Operasi Morfologi

| | |
| --- | --- |
| **Nama** | Andika Wahyu Dwi Saputra |
| **NIM** | 25/557982/PA/23452 |
| **Mata Kuliah** | Pengolahan Citra Digital |
| **Tugas** | Assignment 03 |

Proyek ini memproses tiga citra uji dengan thresholding dan operasi morfologi, lalu membandingkan perubahan yang terjadi pada tiap citra.

## Berkas

| Berkas | Isi |
| --- | --- |
| `PCD_Assignment03.ipynb` | Notebook pengolahan citra |
| `PCD_Assignment03_Laporan` | Laporan dokumentasi hasil segmentasi dan operasi morfologi |

## Tujuan

Melihat bagaimana segmentasi dan operasi morfologi bekerja pada citra dengan kondisi berbeda: banyak noise, tekstur tidak beraturan, dan objek besar yang terpisah jelas.

## Citra Masukan

| Gambar | File | Karakteristik |
| --- | --- | --- |
| Gambar 1 | `sample3.bmp` | Objek berbentuk lingkaran dengan banyak noise |
| Gambar 2 | `sample7.bmp` | Kumpulan daun dengan bentuk dan tekstur berbeda |
| Gambar 3 | `sample10.bmp` | Popcorn terang pada latar belakang gelap |

## Alur Pengolahan

1. **Grayscale**: citra RGB diubah menjadi satu nilai intensitas (0 sampai 255).
2. **Thresholding**: nilai ambang 127 menghasilkan citra biner hitam putih. Pada Gambar 2, daun yang gelap dipilih sebagai bagian putih.
3. **Dilation**: memperbesar area putih (area 3 × 3).
4. **Erosion**: memperkecil area putih (area 3 × 3).
5. **Opening**: erosion lalu dilation, untuk mengurangi noise putih kecil. `A ○ B = (A ⊖ B) ⊕ B`
6. **Closing**: dilation lalu erosion, untuk menutup lubang dan celah kecil. `A • B = (A ⊕ B) ⊖ B`
7. **Kombinasi**: opening dilanjutkan closing.
8. **Penyimpanan**: setiap hasil disimpan dalam format BMP (grayscale, thresholding, dilation, erosion, opening, closing, dan kombinasi).

## Ringkasan Hasil

Jumlah piksel putih sebelum dan sesudah kombinasi opening dan closing:

| Gambar | Sebelum | Sesudah | Selisih | Perubahan |
| --- | --- | --- | --- | --- |
| Gambar 1 | 84.620 | 69.768 | 14.852 | 17,55% |
| Gambar 2 | 79.499 | 74.335 | 5.164 | 6,50% |
| Gambar 3 | 43.802 | 43.772 | 30 | 0,07% |

- **Gambar 1** berubah paling besar karena banyak noise kecil yang terhapus, tetapi sebagian noise berukuran besar masih tersisa.
- **Gambar 2** berubah sedang: tepi dan detail kecil daun menjadi lebih sederhana.
- **Gambar 3** hampir tidak berubah karena popcorn berukuran besar dan terpisah jelas.

## Kesimpulan

Dilation memperbesar area putih dan erosion memperkecilnya. Opening mengurangi noise putih kecil, closing menutup celah sempit, dan kombinasinya membuat citra biner lebih rapi. Besar perubahan bergantung pada bentuk objek, tekstur, tingkat noise, dan jarak antarobjek pada tiap citra.
