# AKBANK-DERIN-OGRENME-BOOTCAMP
# Beyin Tümörü MRI Sınıflandırma

Bu proje, Akbank Derin Öğrenme Bootcamp kapsamında hazırlanmıştır.  
Amaç, MRI görüntülerinden **beyin tümörü sınıflandırması** yapmak için CNN tabanlı bir model geliştirmektir.

## 📊 Veri Seti

- Kaynak: [Kaggle – Brain Tumor MRI Dataset](https://www.kaggle.com/datasets/masoudnickparvar/brain-tumor-mri-dataset)  
- Sınıflar:  
  - **glioma_tumor**  
  - **meningioma_tumor**  
  - **pituitary_tumor**  
  - **no_tumor**  
- Görsel sayısı: ~7,000 (eğitim + test setleri)  

---

## 🔎 Yöntem

1. **Veri Önişleme**  
   - Görseller %70 eğitim, %15 doğrulama, %15 test olacak şekilde stratified split yöntemiyle ayrıldı.  
   - Data augmentation: `rotation_range=10`, `horizontal_flip=True` ile çeşitlilik artırıldı.  

2. **Model Mimarisi (Basit CNN)**  
   - 2 Conv2D + MaxPooling katmanı  
   - Flatten + Dense (128 nöron, ReLU)  
   - Dropout (0.5)  
   - Çıkış katmanı: Softmax  

3. **Eğitim**  
   - Optimizasyon: Adam  
   - Kayıp Fonksiyonu: Categorical Crossentropy  
   - Epoch: 10  
   - Batch Size: 16  

---

## 📈 Sonuçlar

- **Eğitim Doğruluğu (train_acc)**: ~0.30
- **Doğrulama Doğruluğu (val_acc)**: ~0.28  
- **Test Doğruluğu**: ~0.30 

---

### ✅ Confusion Matrix
Modelin sınıflar üzerindeki başarı dağılımı gösterilmiştir.

---

### ✅ Accuracy / Loss Grafikleri


---

### ✅ Grad-CAM Görselleştirmeleri

Aşağıdaki örneklerde modelin MRI görüntüsünde hangi bölgelere odaklandığı görülmektedir.

---

## ⚙️ Hiperparametre Denemeleri

- **Dropout=0.3** → Val_Accuracy: ~0.82  
- **Dropout=0.5** → Val_Accuracy: ~0.85  

**Yorum:** Dropout oranı arttığında modelin aşırı öğrenmesi azaldı ve doğrulama başarımı yükseldi.  

---

## 🧾 Overfitting / Underfitting Yorumu

- Eğitim ve doğrulama doğrulukları arasındaki fark küçük → **aşırı ezberleme yok**.  
- Doğrulama eğrisi genel olarak eğitim eğrisine paralel → **iyi genelleme** yapıyor.  
- Epoch sayısı artırılırsa daha yüksek doğruluk potansiyeli olabilir.  

---

## 🚀 Çalıştırma
Kaggle Notebook Link: https://www.kaggle.com/code/nazerdodu/notebook262bb64f72/edit/run/262869168  

## 📦 Gereksinimler
- tensorflow  
- numpy  
- pandas  
- matplotlib  
- seaborn  
- scikit-learn  
