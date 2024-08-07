# Makine Öğrenimi İle Konut-Fiyat Analizi

Bu proje, İstanbul’un Beylikdüzü bölgesindeki emlak ilanlarını toplama, veri temizleme, dönüştürme ve modelleme adımlarını içerir.

## İçindekiler

1. [Veri Toplama Adımı](#veri-toplama-adımı)
2. [Veri Temizleme ve Dönüştürme](#veri-temizleme-ve-dönüştürme)
   - [Fiyat Düzenleme](#fiyat-düzenleme)
   - [Boş Değerlerin Doldurulması](#boş-değerlerin-doldurulması)
   - [Nadir ve Yaygın Kategoriler](#nadir-ve-yaygın-kategoriler)
   - [Değişken Kategorileştirme](#değişken-kategorileştirme)
3. [Eğitim ve Test Süreci](#eğitim-ve-test-süreci)
   - [Özellik Seçimi ve Modelleme](#özellik-seçimi-ve-modelleme)
   - [Veri Dönüştürme](#veri-dönüştürme)
4. [Kullanım](#kullanım)

## Veri Toplama Adımı

İstanbul’un Beylikdüzü bölgesindeki emlak ilanlarını toplamak için Selenium kütüphanesini kullanıldı.

## Veri Temizleme ve Dönüştürme

### Fiyat Düzenleme

- **Sütun Güncellemeleri:** `PRICE`, `IS_IT_VIEWABLE`, ve `WHO_IS_THE_SELLER` sütunlarındaki değerler döngüler kullanılarak güncellenir.
- **Fiyatın Temizlenmesi:** Fiyat sütunundaki gereksiz karakterler temizlenir ve sayısal veri tipine dönüştürülür. `.replace(".", "")` ve `.str[:-20]` işlemleri, fiyat değerlerini standart bir formatta tutmak için kullanılır.

### Boş Değerlerin Doldurulması

- **Balkon ve Kat Bilgisi:** Boş değerler, `HOUSE_TYPE` sütunundaki bilgiler kullanılarak doldurulur. Örneğin, `IS_THERE_BALCONY` boşsa, "Var" olarak güncellenir.
- **Kat Bilgisi Güncellemeleri:** Boş olan `FLOOR_LOCATION` değerleri, `TOTAL_NUMBER_OF_FLOORS` bilgisi kullanılarak doldurulur.

### Nadir ve Yaygın Kategoriler

- **Nadir Kategoriler:** `NUMBER_OF_ROOMS` ve `TYPE_OF_HEATING` gibi nadir değerler "HIGH_RARITY" veya "Rare" ile güncellenir.
- **Sık Kullanılan Kategoriler:** Sık kullanılan değerler gruplandırılır.

### Değişken Kategorileştirme

- **Kategorik Değerler:** Kategorik sütunlar sayısal değerlerle temsil edilir. Örneğin, `HOUSE_TYPE`, `IS_THERE_BALCONY`, ve `TYPE_OF_HEATING` sütunlarındaki kategoriler sayısal değerlere dönüştürülür.

## Eğitim ve Test Süreci

### Özellik Seçimi ve Modelleme

- **Eğitim ve Test Verileri:** `train_test_split` fonksiyonu ile veriler eğitim ve test setlerine ayrılır.
- **Regresyon ve Sınıflandırma Modelleri:** Modelin başarısı ortalama karesel hata (MSE) gibi metriklerle değerlendirilir. Özelliklerin önem düzeyleri görselleştirilir.

### Veri Dönüştürme

- **One-Hot Encoding:** Kategorik veriler sayısal verilere dönüştürülür. `pd.get_dummies` veya benzeri fonksiyonlar kullanılır.
- **Ölçeklendirme:** `RobustScaler` gibi yöntemlerle veri ölçeklendirilir.


Projeye öneri veya katkıda bulunmak isterseniz, [Linkedin](https://www.linkedin.com/in/ibrahimsezginim) profilimi ziyaret edebilir veya [e-posta](mailto:benibrahimsezgin@outlook.com) ile bana ulaşabilirsiniz.
