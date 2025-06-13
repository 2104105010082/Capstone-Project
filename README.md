# Klasifikasi Gambar CIFAR-10 Menggunakan MobileNetV2 dengan Transfer Learning

## 📌 Deskripsi Proyek

Proyek ini merupakan implementasi pembelajaran mesin untuk melakukan **klasifikasi gambar** menggunakan dataset **CIFAR-10** dan model **MobileNetV2**. Pendekatan yang digunakan adalah **Transfer Learning** dengan memanfaatkan model pralatih dari TensorFlow untuk meningkatkan akurasi dan efisiensi pelatihan.

## 🎯 Tujuan

- Membangun model klasifikasi gambar berdasarkan 10 kelas pada dataset CIFAR-10.
- Menggunakan arsitektur MobileNetV2 sebagai fitur extractor dengan transfer learning.
- Mengevaluasi performa model menggunakan metrik seperti akurasi, confusion matrix, dan classification report.

## 🛠️ Teknologi yang Digunakan

- **Python 3**
- **TensorFlow & Keras**
- **MobileNetV2** (dengan bobot ImageNet)
- **OpenCV** (pengolahan gambar)
- **Scikit-learn** (evaluasi model)
- **Matplotlib & Seaborn** (visualisasi)

## 📂 Struktur Proyek

```
Capstone.ipynb
README.md
```

- `Capstone.ipynb`: Notebook utama berisi seluruh proses mulai dari preprocessing, pelatihan model, hingga evaluasi.
- `README.md`: Dokumentasi proyek ini.

## 🚀 Cara Menjalankan Proyek

1. Unduh repository ini atau salin file notebook ke dalam lingkungan kerja Anda.
2. Instal pustaka yang dibutuhkan:
   ```bash
   pip install tensorflow opencv-python scikit-learn matplotlib seaborn
   ```
3. Buka dan jalankan file notebook:
   ```bash
   jupyter notebook Capstone.ipynb
   ```
4. Jalankan sel notebook secara berurutan untuk memuat data, melakukan preprocessing, melatih model, dan mengevaluasi hasilnya.

## 🧠 Rincian Model

- **Arsitektur**: MobileNetV2 (pralatih dari ImageNet)
- **Ukuran Input**: Gambar CIFAR-10 diskalakan agar sesuai dengan input MobileNetV2 (contoh: 96x96 piksel)
- **Layer Pralatih**: Dibekukan (non-trainable) selama pelatihan
- **Kepala Klasifikasi**: Tambahan Dense layers di atas MobileNetV2
- **Optimizer**: Adam
- **Loss Function**: Categorical Crossentropy
- **Metrik Evaluasi**: Akurasi

## 📊 Hasil & Evaluasi

- Model dilatih menggunakan EarlyStopping dan pengurangan learning rate otomatis.
- Evaluasi mencakup:
  - **Classification Report**
  - **Confusion Matrix**
  - **Visualisasi Akurasi dan Loss**

Hasil akurasi dan grafik evaluasi selengkapnya dapat dilihat langsung di dalam notebook.

## 📸 Contoh Hasil

- Plot kurva akurasi dan loss saat training dan validasi.
- Confusion matrix dalam bentuk heatmap.
- Visualisasi prediksi label pada gambar.

## 📚 Referensi

- [Dokumentasi TensorFlow MobileNetV2](https://www.tensorflow.org/api_docs/python/tf/keras/applications/MobileNetV2)
- [Dataset CIFAR-10](https://www.cs.toronto.edu/~kriz/cifar.html)
- [Tutorial Transfer Learning TensorFlow](https://www.tensorflow.org/tutorials/images/transfer_learning)
