# 🦴 KemikAI — Çocuklarda Multimodal Kemik Gelişim Analizi

> El röntgeni görüntüsü ve klinik veriler kullanılarak çocuklarda kemik yaşı tahmin eden, gelişim durumu raporlayan ve GradCAM ile açıklanabilir yapay zeka sunan multimodal derin öğrenme sistemi.

![Python](https://img.shields.io/badge/Python-3.10-blue)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.20-orange)
![Gradio](https://img.shields.io/badge/Arayüz-Gradio-purple)
![MAE](https://img.shields.io/badge/Val%20MAE-5.59%20ay-green)

---

## 🎯 Proje Nedir?

KemikAI, bir çocuğun el röntgeni görüntüsünü ve klinik bilgilerini alarak:

- 🦴 **Kemik yaşını tahmin eder** (ay ve yıl cinsinden)
- 📊 **Gelişim durumunu raporlar** (Normal / Geride / İleride)
- 🔬 **GradCAM ısı haritası üretir** (modelin hangi bölgeye odaklandığını gösterir)
- 📋 **Klinik rapor oluşturur** (tüm bilgiler tek ekranda)

---

## 🧠 Model Mimarisi
Görüntü Dalı: El Röntgeni (224x224x3) → EfficientNetV2S → GlobalAvgPool → Dense(256)
↓
Concatenate
↑
Tabular Dal:  8 Klinik Özellik → Dense(64) → Dense(32) ————————————————————————————
↓
Dense(128) → Dense(1) → Kemik Yaşı (ay)

**8 Klinik Özellik:** Cinsiyet · Boy · Kilo · Anne Boyu · Baba Boyu · D Vitamini · Kalsiyum · Kırık Geçmişi

---

## 📊 Performans

| Model | Val MAE | Val MAE (yıl) |
|-------|---------|---------------|
| Tek Girdili (sadece görüntü) | 8.28 ay | 0.69 yıl |
| **KemikAI Multimodal** | **5.59 ay** | **0.47 yıl** |

> Multimodal model, tek girdili modele kıyasla **%32.5 daha iyi** performans sergiledi.

---

## 📁 Proje Yapısı

| Dosya | Açıklama |
|-------|----------|
| `notebooks/01_setup.ipynb` | Ortam kurulumu, Kaggle API, Drive bağlantısı |
| `notebooks/02_eda.ipynb` | Veri keşfi, dağılım grafikleri |
| `notebooks/03_preprocessing.ipynb` | Görüntü işleme, sentetik klinik veri üretimi |
| `notebooks/04_model.ipynb` | İlk model denemesi (tek girdi) |
| `notebooks/05_training_multimodal.ipynb` | Multimodal model eğitimi — ana eğitim dosyası |
| `notebooks/06_evaluation.ipynb` | Model değerlendirme, MAE hesaplama, grafikler |
| `notebooks/07_gradcam.ipynb` | GradCAM ısı haritası görselleştirme |
| `notebooks/08_gradio_app.ipynb` | Gradio interaktif arayüz |
| `outputs/plots/` | EDA ve değerlendirme grafikleri |
| `outputs/gradcam/` | GradCAM çıktı görselleri |
| `requirements.txt` | Gerekli kütüphaneler |

---

## 🚀 Nasıl Çalıştırılır?

### 1. Gereksinimler
```bash
pip install -r requirements.txt
```

### 2. Veri Seti
[RSNA Pediatric Bone Age](https://www.kaggle.com/datasets/kmader/rsna-bone-age) veri setini Kaggle'dan indirin.

### 3. Notebook Sırası
01_setup → 02_eda → 03_preprocessing → 05_training_multimodal → 06_evaluation → 07_gradcam → 08_gradio_app

### 4. Arayüzü Başlat
`08_gradio_app.ipynb` dosyasını çalıştırın. Gradio linki otomatik oluşacaktır.

---

## 🔬 GradCAM Nedir?

GradCAM, modelin kararını verirken görüntünün **hangi bölgesine odaklandığını** ısı haritasıyla görselleştirir. KemikAI'da modelin büyüme plakaları ve bilek bölgelerine odaklandığı gözlemlenmiştir — bu klinik olarak anlamlı bir bulgudur.

---

## 🛠️ Teknolojiler

| Araç | Kullanım |
|------|----------|
| TensorFlow / Keras | Model eğitimi |
| EfficientNetV2S | Transfer learning backbone |
| Gradio | İnteraktif web arayüzü |
| OpenCV | GradCAM görselleştirme |
| Scikit-learn | Veri ön işleme (StandardScaler) |
| Google Colab T4 GPU | Eğitim ortamı |

---

## 📚 Kaynaklar

- Halabi et al. (2019). The RSNA Pediatric Bone Age Machine Learning Challenge. *Radiology.*
- Selvaraju et al. (2017). Grad-CAM: Visual Explanations from Deep Networks. *ICCV.*
- Tan & Le (2021). EfficientNetV2: Smaller Models and Faster Training. *ICML.*

---
