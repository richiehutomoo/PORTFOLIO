# Eksplorasi Data dan Penghapusan Outlier dengan Metode IQR

Berikut adalah eksplorasi mendalam mengenai data `Indonesia Reading Interest`, termasuk langkah-langkah preprocessing dan penghapusan outlier menggunakan metode Interquartile Range (IQR).

-----

### 1\. Eksplorasi dan Pra-pemrosesan Data Awal

Berdasarkan dataset `TGM 2020-2023_eng.csv`, langkah pertama adalah membersihkan data. Beberapa kolom numerik, seperti frekuensi membaca dan durasi, memiliki tipe data **object** karena menggunakan koma (`,`) sebagai pemisah desimal. Saya telah memodifikasi kode untuk mengubahnya menjadi titik (`.`) agar dapat diolah sebagai tipe data **float**.

-----

### 2\. Memahami Metode IQR (Interquartile Range)

Metode IQR adalah teknik statistik untuk mengidentifikasi data pencilan (outlier) yang berada jauh dari nilai pusat data. Cara kerjanya cukup sederhana:

1.  **Kuartil ($Q1$ dan $Q3$):** Pertama, data diurutkan dan dibagi menjadi empat bagian. $Q1$ adalah median dari separuh data pertama (persentil ke-25), sedangkan $Q3$ adalah median dari separuh data terakhir (persentil ke-75).
2.  **IQR:** Dihitung sebagai selisih antara $Q3$ dan $Q1$.
    $$IQR = Q3 - Q1$$
3.  **Batas (Boundaries):** Outlier adalah data yang berada di luar batas bawah dan batas atas yang ditentukan oleh formula ini:
      * Batas Bawah: $Q1 - 1.5 \\times IQR$
      * Batas Atas: $Q3 + 1.5 \\times IQR$

Metode ini efektif untuk mengeliminasi nilai-nilai ekstrem yang dapat memengaruhi analisis statistik.

-----

### 3\. Eksperimen Penghapusan Outlier dan Hasilnya

Saya menerapkan metode IQR pada kolom-kolom numerik yang relevan. Hasilnya menunjukkan beberapa outlier berhasil diidentifikasi dan dihapus, seperti yang dirangkum di bawah ini:

  * **Reading Frequency per week**: 13 outliers dihapus.
  * **Number of Readings per Quarter**: 0 outliers dihapus.
  * **Daily Reading Duration (in minutes)**: 3 outliers dihapus.
  * **Internet Access Frequency per Week**: 8 outliers dihapus.
  * **Daily Internet Duration (in minutes)**: 2 outliers dihapus.
  * **Tingkat Kegemaran Membaca (Reading Interest)**: 1 outlier dihapus.

Setelah proses ini, dataset yang sudah bersih disimpan dalam file baru bernama `TGM_2020-2023_cleaned_with_IQR.csv`.

-----

### 4\. Perbandingan Distribusi Data

Untuk melihat efek dari penghapusan outlier, berikut adalah perbandingan visual melalui histogram. Perhatikan bagaimana distribusi data menjadi lebih terpusat dan rapi setelah outlier dihilangkan.

#### Histogram Data Asli (Sebelum Penghapusan Outlier)

#### Histogram Data yang Sudah Dibersihkan (Sesudah Penghapusan Outlier)

Seperti yang terlihat, histogram data yang dibersihkan memiliki rentang nilai yang lebih sempit dan lebih terfokus, menunjukkan bahwa data outlier telah berhasil dikeluarkan.

-----
