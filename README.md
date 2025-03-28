# **EDGE DETECTION**

## **1. Jenis-Jenis Tepi dalam Citra Digital**  

### **Empat Jenis Tepi:**  
1. **Tepi Curam (Step Edge)**  
   - Perubahan intensitas terjadi secara mendadak dan tajam.  
   - **Contoh:** Perbatasan antara dinding hitam dan latar belakang putih.  

2. **Tepi Landai (Ramp Edge)**  
   - Perubahan intensitas terjadi secara bertahap.  
   - **Contoh:** Bayangan pohon yang memudar di atas permukaan tanah.  

3. **Tepi Garis (Line Edge)**  
   - Tepi muncul di antara dua area dengan intensitas serupa, membentuk garis tipis.  
   - **Contoh:** Kabel listrik hitam di langit cerah.  

4. **Tepi Atap (Roof Edge)**  
   - Intensitas meningkat secara perlahan hingga mencapai puncak, lalu menurun kembali.  
   - **Contoh:** Pantulan cahaya pada permukaan bola mengkilap.  

---

## **2. Mengapa Tepi dengan Derau Memerlukan Pendekatan Khusus?**  

### **Masalah yang Ditimbulkan Derau:**  
- **Menyembunyikan tepi yang sebenarnya** → Sulit mengenali tepi utama.  
- **Kesalahan deteksi (false positives)** → Derau dapat dikira sebagai tepi.  
- **Kehilangan tepi asli (false negatives)** → Derau bisa menutupi tepi sebenarnya.  
- **Gangguan perubahan gradien** → Fluktuasi acak mengganggu pendeteksian tepi.  

### **Solusi:**  
- **Filtering:** Gaussian filter atau median filter untuk mengurangi derau sebelum deteksi.  
- **Algoritma Canggih:** Canny Edge Detection dan Laplacian of Gaussian (LoG).  
- **Thresholding:** Menyaring tepi yang signifikan dari noise.  

---

## **3. Pendeteksian Tepi Menggunakan Operator Gradien (Sobel)**  

### **Langkah-langkah:**  
1. **Mengunggah dan Membaca Gambar**  
   - Gambar dikonversi ke grayscale untuk penyederhanaan analisis.  

2. **Menghitung Gradien dengan Operator Sobel**  
   - **Sobel X:** Deteksi tepi horizontal.  
   - **Sobel Y:** Deteksi tepi vertikal.  
   - **Sobel Combined:** Menggabungkan kedua gradien untuk menyoroti tepi secara keseluruhan.  

3. **Menampilkan Hasil Deteksi:**  
   - **Sobel X:** Menyoroti tepi horizontal.  
   - **Sobel Y:** Menyoroti tepi vertikal.  
   - **Sobel Combined:** Menampilkan tepi lengkap dari objek dalam citra.  

---

## **4. Perbandingan Operator Pendeteksi Tepi**  

| Operator | Akurasi Pendeteksian | Kompleksitas Komputasi | Situasi Penggunaan |
|----------|----------------------|------------------------|--------------------|
| **Sobel** | Sedang | Sedang | Tepi yang jelas & analisis cepat |
| **Prewitt** | Rendah | Rendah | Deteksi sederhana & cepat |
| **Canny** | Tinggi | Tinggi | Deteksi tepi presisi tinggi & bebas derau |

### **Kesimpulan:**  
- Gunakan **Sobel** untuk analisis cepat.  
- Gunakan **Prewitt** jika kecepatan lebih diutamakan daripada akurasi.  
- Gunakan **Canny** untuk hasil terbaik dengan deteksi presisi tinggi, terutama jika citra mengandung derau.  

---

## **5. Analisis Hasil Pendeteksian**  

1. **Original Image:** Gambar asli tanpa modifikasi.  
2. **Noisy Image (Salt-and-Pepper):** Citra dengan derau acak yang mengganggu deteksi tepi.  
3. **Gaussian Filtered Image:** Derau berkurang setelah diterapkan Gaussian filter.  
4. **Sobel Edge Detection:**  
   - Deteksi tepi cukup baik, tetapi masih menangkap sedikit derau sebagai tepi palsu.  
   - Kurang efektif dalam menangani perubahan intensitas yang halus atau objek dengan tepi kompleks.  

---

## **Kesimpulan Akhir**  
1. **Deteksi tepi sangat bergantung pada metode yang digunakan.**  
2. **Operator Sobel efektif untuk perubahan intensitas tajam, tetapi kurang optimal dalam menangani derau.**  
3. **Operator Canny lebih direkomendasikan untuk analisis yang lebih akurat karena menangani derau lebih baik.**  
