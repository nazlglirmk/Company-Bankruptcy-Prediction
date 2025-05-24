#  Company Bankruptcy Prediction

Bu projede, şirketlerin finansal verilerine dayanarak iflas edip etmeyeceklerini tahmin eden bir makine öğrenmesi modeli geliştirildi.

##  Problem Tanımı

- **Tür:** Gözetimli Öğrenme - Sınıflandırma  
- **Hedef değişken:** `Bankrupt?`  
  - `0`: Şirket iflas etmedi  
  - `1`: Şirket iflas etti

> Veri dengesiz:  
> - %96.77 iflas etmedi  
> - %3.23 iflas etti

## Veri Kümesi

- Gözlem sayısı: 6819  
- Özellik sayısı: 96  
- Veri tipi: Finansal oranlar (ROA, kar marjı, borç/sermaye oranı vb.)  
- Eksik veri bulunmamaktadır.

##  EDA (Keşifsel Veri Analizi)

- `countplot` ve istatistiksel özetler ile veri dağılımı incelendi.
- Hedef değişken ile en yüksek korelasyona sahip öznitelikler belirlendi:
  - `Debt ratio %` (~0.25)
  - `Borrowing dependency`
  - `Liability to Equity`
  - vb.

## Kullanılan Modeller

| Model               | İflas Edenleri Yakalama (Recall) | Genel Doğruluk |
|--------------------|-----------------------------------|----------------|
| Karar Ağacı        | %29                              | %96            |
| Lojistik Regresyon | **%97**                          | %87            |
| Rastgele Orman     | %13                              | %97            |



##  Sonuçlar ve Öneriler

- **Azınlık sınıfı** (iflas edenler) için en yüksek başarı: **Lojistik Regresyon**
- **Dengeli genel başarı**: Karar Ağacı
- **Zayıf iflas tahmini**: Random Forest

Bu proje, özellikle bankacılık ve kredi riski analizleri gibi alanlarda kullanılabilecek bir iflas tahmin sistemi geliştirmeyi amaçlar.

##  Geliştirme Önerileri

- SMOTE gibi over/under sampling yöntemleriyle sınıf dengesizliği iyileştirilebilir.
- ROC-AUC analizi eklenebilir.
- Model web arayüzü (Flask, Streamlit) ile sunulabilir.



