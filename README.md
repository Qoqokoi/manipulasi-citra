Timpa file README.md Anda dengan arsitektur ini. Sembilan parameter regulasi telah diinjeksi secara presisi tanpa celah.Markdown# Manipulasi Citra Digital: Operasi Matriks OpenCV

**Diarsipkan oleh:** Muhammad Dafi Al Haq
**Program Studi:** Teknik Informatika

## 1. Deskripsi Singkat Project
Proyek ini mengeksekusi manipulasi level atomik pada matriks citra digital. Operasi berfokus pada fusi aljabar linier dan pemetaan non-linier menggunakan arsitektur memori `uint8`. Tujuannya bukan sekadar penyuntingan visual, melainkan ekstraksi data sinyal pada area *underexposed* ekstrem dan mitigasi distorsi matriks (*integer overflow*).

## 2. Citra yang Digunakan
Sistem memproses dua aset matriks utama:
* **Citra 1 (Target Transformasi):** Objek manusia dengan pendaran lampu LED dalam kondisi *underexposed* (gelap mayoritas).
* **Citra 2 (Target Fusi):** Lingkungan jalanan dengan tekstur rintik hujan dan pantulan cahaya (*high-frequency signal*).

## 3. Library yang Digunakan
* **Python 3.x:** Kernel eksekusi utama.
* **OpenCV (`cv2`):** Dekoding ruang warna dan manipulasi spasial matriks.
* **NumPy (`numpy`):** Komputasi aljabar linier dan array multi-dimensi.
* **Matplotlib (`matplotlib.pyplot`):** Rendering arsitektur visual dan ekstraksi histogram.

## 4. Cara Menjalankan Notebook
1. Kloning repositori ke mesin lokal Anda:
   ```bash
   git clone [https://github.com/username/manipulasi-citra-opencv.git](https://github.com/username/manipulasi-citra-opencv.git)
   cd manipulasi-citra-opencv
Injeksi dependensi komputasi:Bashpip install opencv-python numpy matplotlib jupyter
Bangunkan server komputasi Jupyter:Bashjupyter notebook
Buka file manipulasi_citra.ipynb di browser dan eksekusi seluruh sel komputasi secara berurutan (Shift + Enter).5. Struktur Folder ProjectPlaintext├── image1.jpg                # Aset matriks primer (Gelap)
├── image2.jpg                # Aset matriks sekunder (Tekstur)
├── manipulasi_citra.ipynb    # Pipeline komputasi utama
├── laporan_analitik.pdf      # Dokumen analisis HOTS komprehensif
└── README.md                 # Dokumentasi operasional sistem
6. Ringkasan Hasil EksperimenKonversi & Resize: Standardisasi dimensi ke 600x400 dan routing ulang BGR ke RGB berhasil mengembalikan rasio aspek dan spektrum warna asli.Image Blending: Fusi dua matriks berhasil dilakukan tanpa distorsi overexposed. Dominasi visual berubah secara presisi mengikuti rasio bobot skalar ($\alpha$ dan $\beta$).Image Negative: Inversi polaritas piksel tereksekusi sempurna, mencerminkan kurva histogram secara simetris dari spektrum gelap ke terang.Transformasi Logaritmik: Fungsi $s = c \log(1+r)$ sukses menarik rentang piksel gelap secara agresif, mengekspos geometri objek yang sebelumnya buta, namun memicu noise amplification.Transformasi Gamma: Parameter eksponensial ($\gamma < 1$) mendongkrak visibilitas mid-tones, sementara ($\gamma > 1$) meremukkan nilai piksel ke dasar lantai matriks.7. Kesimpulan SingkatManipulasi citra adalah mitigasi kalkulasi aljabar untuk mempertahankan integritas data pada limitasi arsitektur 8-bit (255). Algoritma Logaritmik terbukti sebagai metode brute-force paling efisien untuk ekstraksi sinyal pada kegelapan ekstrem, sementara Koreksi Gamma lebih fleksibel untuk distribusi cahaya tingkat menengah tanpa merusak white point. Kegagalan menyamakan dimensi atau tipe data array akan selalu memicu kegagalan sistem (fatal error).
