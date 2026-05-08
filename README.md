# 🦴 KemikAI — Çocuklarda Kemik Gelişim Analizi

El röntgeni görüntüsü ve klinik verilerle kemik yaşı tahmini yapan multimodal derin öğrenme sistemi.

## 📊 Model Performansı
- **Validation MAE:** 5.59 ay (0.47 yıl)
- **Mimari:** EfficientNetV2S + Tabular Branch (Dual-Input)
- **Veri Seti:** RSNA 2017 Pediatric Bone Age (12.611 görüntü)

## 🚀 Özellikler
- El röntgeni + 8 klinik özellik (boy, kilo, anne/baba boyu, D vitamini, kalsiyum, kırık geçmişi)
- GradCAM görselleştirme
- Gelişim durumu raporu (Normal / Geride / İleride)
- Gradio tabanlı interaktif arayüz

## 📁 Proje Yapısı
notebooks/01_setup.ipynb
notebooks/02_eda.ipynb
notebooks/03_preprocessing.ipynb
notebooks/04_model.ipynb
notebooks/05_training_multimodal.ipynb
notebooks/06_evaluation.ipynb
notebooks/07_gradcam.ipynb
notebooks/08_gradio_app.ipynb

## 🛠️ Kurulum
pip install -r requirements.txt

## 📚 Kaynaklar
- RSNA Bone Age Dataset: https://www.kaggle.com/datasets/kmader/rsna-bone-age
- EfficientNetV2: https://arxiv.org/abs/2104.00298
