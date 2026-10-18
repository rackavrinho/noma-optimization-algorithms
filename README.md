# NOMA Optimization Algorithms

Repository ini berisi notebook Python untuk simulasi alokasi subcarrier dan daya transmisi pada jaringan *downlink* Non-Orthogonal Multiple Access (NOMA). Fokusnya adalah membandingkan nilai **Weighted Sum Rate (WSR)** dan waktu komputasi dari beberapa algoritma.

Notebook menggunakan implementasi JSPA dari [repository Nokia](https://github.com/nokia/subcarrier-power-allocation-noma-solver) sebagai referensi, lalu menambahkan beberapa metode optimasi untuk kebutuhan eksperimen.

## Isi notebook

- **Channel Model & Gains:** membangkitkan kondisi kanal, gain, dan derau untuk simulasi.
- **SCPC & SCUS:** contoh pengaturan daya dan pemilihan pengguna pada satu subcarrier.
- **JSPA:** pengujian OPT-JSPA, ε-JSPA, Grad-JSPA, dan *equal-power allocation*.
- **Algoritma pembanding:** Particle Swarm Optimization (PSO), Genetic Algorithm (GA), Teaching–Learning-Based Optimization (TLBO), Tawuran Strategy Optimization (TSO), dan War Takjil Optimization (WTO).
- **Evaluasi:** membandingkan WSR, waktu eksekusi, grafik konvergensi, dan perubahan WSR saat batas daya transmisi dinaikkan.

TSO dan WTO merupakan metode eksperimental di notebook ini, bukan bagian dari algoritma referensi Nokia.

## Parameter simulasi

Konfigurasi yang digunakan pada bagian perbandingan algoritma:

| Parameter | Nilai |
| --- | --- |
| Jumlah pengguna (`K`) | 5 |
| Jumlah subcarrier (`L`) | 10 |
| Maksimum pengguna per subcarrier | 2 |
| Bandwidth | 5 MHz |
| Total daya transmisi (`Pmax`) | 1 W |
| Radius sel | 1.000 m |
| Jarak minimum pengguna | 35 m |
| Random seed | 42 |

Pada pengujian variasi daya, `Pmax` diubah dari **0,10 W sampai 1,00 W** dengan interval **0,05 W**. Bagian contoh SCPC, SCUS, dan JSPA di awal notebook menggunakan parameter tersendiri.

## Hasil pengujian

Notebook menampilkan tabel WSR dan waktu komputasi untuk tiap metode, grafik proses optimasi PSO/GA/TLBO/TSO, serta grafik WSR terhadap `Pmax` untuk OPT-JSPA, Grad-JSPA, PSO, GA, TLBO, dan WTO.

Output yang tersimpan menunjukkan perbedaan WSR cukup besar antara metode JSPA dan beberapa metode berbasis populasi. Hasil ini masih perlu diperiksa dengan pengujian ulang dan penyamaan cara evaluasi sebelum digunakan untuk menyimpulkan algoritma mana yang paling baik. Waktu komputasi juga bergantung pada lingkungan yang digunakan.

## Menjalankan notebook

**Google Colab**

1. Buka file [`NOMA_Optimization_Algorithms.ipynb`](NOMA_Optimization_Algorithms.ipynb) dari repository ini.
2. Pilih **Open in Colab**, jika tersedia, atau buka [Google Colab](https://colab.research.google.com/) lalu pilih **File → Open notebook → GitHub**.
3. Jalankan seluruh sel secara berurutan melalui **Runtime → Run all**.

**Jupyter Notebook (lokal)**

```bash
python -m pip install numpy matplotlib notebook
jupyter notebook NOMA_Optimization_Algorithms.ipynb
```

Tidak ada dataset yang perlu diunduh karena data kanal dibuat langsung dalam simulasi. Jalankan sel dari atas ke bawah karena beberapa fungsi dan variabel dipakai kembali pada sel berikutnya.

## Referensi

- L. Salaün, M. Coupechoux, dan C. S. Chen, “Joint Subcarrier and Power Allocation in NOMA: Optimal and Approximate Algorithms,” *IEEE Transactions on Signal Processing*, 2020. [DOI](https://doi.org/10.1109/TSP.2020.2982786).
- Kode referensi: [Nokia — subcarrier-power-allocation-noma-solver](https://github.com/nokia/subcarrier-power-allocation-noma-solver).

Kode referensi Nokia mencantumkan lisensi **CC BY-NC 4.0**. Atribusi dan ketentuan lisensi tersebut tetap berlaku untuk bagian kode yang digunakan dari sumber aslinya.
