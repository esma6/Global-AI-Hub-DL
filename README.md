# Global-AI-Hub-DL Bootcamp
# CNN ve Transfer Öğrenme Modelleri ile Beyin Tümörü MRI Sınıflandırması

## 📌 Proje Hakkında
Bu proje, **MRI beyin tümörü görüntülerinin sınıflandırılması** amacıyla geliştirilmiştir.  
Hem **Convolutional Neural Network (CNN)** hem de **Transfer Learning (ResNet50)** yaklaşımları kullanılarak farklı model performansları karşılaştırılmıştır.  
Ayrıca, model hiperparametre optimizasyonu için **Keras Tuner RandomSearch** uygulanmıştır.  

---

## 🗂️ Veri Seti
- **Kaynak:** [Brain Tumor MRI Dataset - Kaggle](https://www.kaggle.com/navoneel/brain-mri-images-for-brain-tumor-detection)  
- **Sınıflar:**
  - `glioma_tumor`
  - `meningioma_tumor`
  - `pituitary_tumor`
  - `no_tumor`

---

## 🛠️ Kullanılan Teknolojiler
- Python 3.9+
- TensorFlow / Keras
- PyTorch (bazı ön işleme adımları için)
- scikit-learn
- Matplotlib & Seaborn
- PIL (Python Imaging Library)
- OpenCV (Grad-CAM görselleştirmeleri için)

---

## 🔧 Proje Adımları

### 1️⃣ Veri Hazırlığı ve Görselleştirme
- Sınıf dağılımları kontrol edildi ve görselleştirildi.  
- Örnek görüntüler incelendi.  


### 2️⃣ Veri Ön İşleme

Görüntüler normalize edildi (0-1 aralığına çekildi).

One-hot encoding ile etiketler hazırlandı.

Train/Validation split gerçekleştirildi.

### 3️⃣ Veri Artırma (Data Augmentation)

Rastgele yatay çevirme, döndürme, zoom ve translation uygulanarak modelin farklı varyasyonlara karşı dayanıklılığı artırıldı.

### 4️⃣ CNN Modeli Eğitimi

Basit bir CNN mimarisi kuruldu:

3 adet Conv2D + MaxPooling2D katmanı

Flatten → Dense → Dropout → Softmax çıkış

EarlyStopping ve ModelCheckpoint ile eğitim optimize edildi.

### 5️⃣ Transfer Learning

ResNet50 önceden eğitilmiş modeli kullanıldı (include_top=False)

GlobalAveragePooling → Dense → Dropout → Softmax ile sınıflandırma katmanı eklendi.

Base model freeze edilerek sadece üst katmanlar eğitildi.

### 6️⃣ Hiperparametre Optimizasyonu

Keras Tuner RandomSearch kullanıldı.

Denenen parametreler:

Conv katman sayısı: 2-4

Filtre sayısı: 32, 64, 128

Dense units: 64-256

Dropout oranı: 0.2-0.5

Learning rate: 1e-4 – 1e-2

RandomSearch ile en iyi model seçildi.

### 7️⃣ Model Değerlendirme

Test setinde accuracy ve loss ölçüldü.

Confusion Matrix ve Classification Report ile detaylı sınıf bazlı performans analiz edildi.

### 8️⃣ Grad-CAM ile Görselleştirme

Modelin hangi bölgelerden etkilendiği görselleştirildi.

# ⚡ Kurulum ve Çalıştırma

### Sanal ortam oluştur
#### python -m venv venv
#### source venv/bin/activate  # Linux / Mac
#### venv\Scripts\activate     # Windows

### Gerekli paketleri yükle
pip install -r requirements.txt

### Jupyter Notebook başlat
jupyter notebook

---
#  Proje Linki

**Proje:** [Brain Tumor MRI Classification - Kaggle](https://www.kaggle.com/code/esmakaraglle/notebook90cbfd162f)  


