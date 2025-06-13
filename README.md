
# Klasifikasi Gambar CIFAR-10 Menggunakan MobileNetV2 dengan Transfer Learning

## 📌 Deskripsi Proyek

Proyek ini merupakan implementasi pembelajaran mesin untuk melakukan **klasifikasi gambar** menggunakan dataset **CIFAR-10** dan model **MobileNetV2**. Pendekatan yang digunakan adalah **Transfer Learning** dengan memanfaatkan model pralatih dari TensorFlow untuk meningkatkan akurasi dan efisiensi pelatihan.

## 🎯 Tujuan

- Membangun model klasifikasi gambar berdasarkan 10 kelas pada dataset CIFAR-10.
- Menggunakan arsitektur MobileNetV2 sebagai fitur extractor dengan transfer learning.
- Mengevaluasi performa model menggunakan metrik seperti akurasi, confusion matrix, dan classification report.
- Mendeploy model ke dalam format **TensorFlow Lite (TFLite)** agar dapat digunakan pada perangkat mobile atau embedded system.

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
saved_model/
├── cifar_model/             # Folder berisi model SavedModel TensorFlow
cifar_model.tflite           # File model setelah dikonversi ke TFLite
```

- `Capstone.ipynb`: Notebook utama berisi seluruh proses mulai dari preprocessing, pelatihan model, evaluasi, hingga konversi TFLite.
- `README.md`: Dokumentasi proyek ini.

## 🚀 Cara Menjalankan Proyek

1. Unduh repository ini atau salin file notebook ke dalam lingkungan kerja Anda.
2. Instal pustaka yang dibutuhkan:
   ```bash
   pip install tensorflow opencv-python scikit-learn matplotlib seaborn
   ```

3. Jalankan notebook:

   ```bash
   jupyter notebook Capstone.ipynb
   ```
4. Ikuti setiap langkah dari preprocessing hingga evaluasi model.

## 📥 Deploy ke TensorFlow Lite

Model yang telah dilatih dikonversi ke format TFLite menggunakan kode berikut:

```python
import tensorflow as tf

# Konversi model ke format TFLite
converter = tf.lite.TFLiteConverter.from_saved_model("saved_model/cifar_model")
tflite_model = converter.convert()

# Simpan model TFLite
with open("cifar_model.tflite", "wb") as f:
    f.write(tflite_model)
```

### 📱 Cara Menggunakan Model TFLite (Contoh Inference Python)

```python
import tensorflow as tf
import numpy as np

# Load model TFLite
interpreter = tf.lite.Interpreter(model_path="cifar_model.tflite")
interpreter.allocate_tensors()

input_details = interpreter.get_input_details()
output_details = interpreter.get_output_details()

# Contoh input (gambar CIFAR-10 sudah diproses dan diskalakan ke ukuran model)
input_data = np.expand_dims(preprocessed_image, axis=0).astype(np.float32)

# Inference
interpreter.set_tensor(input_details[0]['index'], input_data)
interpreter.invoke()
output_data = interpreter.get_tensor(output_details[0]['index'])

predicted_class = np.argmax(output_data)
```

Model ini dapat digunakan untuk aplikasi mobile Android dengan TensorFlow Lite Interpreter atau diintegrasikan ke IoT/edge-device.

## 🧠 Rincian Model

* **Arsitektur**: MobileNetV2 (pralatih dari ImageNet)
* **Ukuran Input**: Gambar CIFAR-10 diskalakan agar sesuai dengan input MobileNetV2 (contoh: 96x96 piksel)
* **Layer Pralatih**: Dibekukan (non-trainable) selama pelatihan awal
* **Kepala Klasifikasi**: Tambahan Dense layers di atas MobileNetV2
* **Optimizer**: Adam
* **Loss Function**: Categorical Crossentropy
* **Metrik Evaluasi**: Akurasi

## 📊 Hasil & Evaluasi

* Akurasi Validasi: 91.3%
* Akurasi Uji: 90.34%
* Evaluasi mencakup:

  * **Classification Report**
  * **Confusion Matrix**
  * **Visualisasi Akurasi dan Loss**
* Visualisasi prediksi dengan confidence score dan kesalahan klasifikasi.

## 📸 Contoh Hasil

* Plot kurva akurasi dan loss saat training dan validasi.
* Confusion matrix dalam bentuk heatmap.
* Visualisasi prediksi label pada gambar dengan warna indikator benar/salah.

## 📚 Referensi

* [Dokumentasi TensorFlow MobileNetV2](https://www.tensorflow.org/api_docs/python/tf/keras/applications/MobileNetV2)
* [Dataset CIFAR-10](https://www.cs.toronto.edu/~kriz/cifar.html)
* [Tutorial Transfer Learning TensorFlow](https://www.tensorflow.org/tutorials/images/transfer_learning)
* [TensorFlow Lite Guide](https://www.tensorflow.org/lite/guide)
