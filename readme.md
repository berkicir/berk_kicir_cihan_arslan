# Harmoni Arama Algoritması Kullanılarak Kompanzasyon Sistemlerinin Optimizasyonu

**Ders:** Makine Öğrenmesi ve Optimizasyon Mühendislik Uygulamaları  
**Dönem:** 2025 Bahar  
**Kurum:** KTO Karatay Üniversitesi - Mühendislik ve Doğa Bilimleri Fakültesi

## 👥 Proje Ekibi
* **Berk KICIR** - 241451040
* **Cihan ARSLAN** - 231451030
* **Danışman:** Dr. Öğr. Üyesi Esra URAY

---

## 📝 Proje Tanımı ve Problem
Elektrik şebekelerinde enerji verimliliği ve hat güvenliği için reaktif güç kompanzasyonu kritiktir. EPDK ve TEDAŞ mevzuatlarına göre işletmelerin endüktif reaktif oranlarını **%20**, kapasitif oranlarını ise **%15** sınırları içerisinde tutması gerekmektedir.

Ancak, düzensiz kondansatör kademelerine (Örn: 1, 1.5, ..., 60 kVAr) sahip tesislerde geleneksel yöntemler yetersiz kalabilmektedir. Bu proje, **Harmoni Arama Algoritması (Harmony Search Algorithm - HSA)** kullanarak bu problemi "Kısıtlı Kombinatoryal Optimizasyon" problemi olarak modeller ve en uygun kondansatör anahtarlamasını gerçekleştirir.

## 🚀 Kullanılan Yöntem ve Algoritma
Projede **MATLAB** ortamında geliştirilen **Harmony Search Algorithm (HSA)** kullanılmıştır. Algoritma, türev gerektirmeyen yapısı ve ayrık (discrete) değişkenlerdeki başarısı nedeniyle tercih edilmiştir.

### Algoritma Parametreleri:
* **HMS (Harmoni Hafıza Boyutu):** 60
* **HMCR (Hafıza Kabul Oranı):** 0.98 (Kararlı yakınsama için)
* **PAR (Ton Ayarlama Oranı):** 0.45 (Yerel minimumdan kaçış için)
* **Maksimum İterasyon:** 10.000

### Amaç Fonksiyonu (Cost Function):
Sistemin başarısı şu formülize edilmiş ceza fonksiyonu ile ölçülür:
$$Cost = |Q_{yük} - Q_c| + Ceza$$
Burada sistem %20 endüktif veya %15 kapasitif sınırını aşarsa, algoritmaya **100.000** katsayılı çok yüksek bir ceza puanı eklenir. Ayrıca, kontaktör ömrünü uzatmak amacıyla büyük güçlü kondansatörlere ağırlık cezası uygulanarak "hassas" (küçük) kademelerin seçimi teşvik edilir.

## 📊 Sonuçlar
Geliştirilen algoritma iki farklı senaryoda test edilmiştir:

1.  **İdeal Yüklenme (100 kW Aktif / 80 kVAr Endüktif):**
    * Algoritma 10.000 iterasyon sonunda **0.00 kVAr** net hata ile tam kompanzasyon sağlamıştır.
    * Reaktif oran **%0.00** olarak gerçekleşmiştir.
    * Sistem güvenli bölgede tutulmuştur.

2.  **Yetersiz Donanım Senaryosu:**
    * Donanım sınırlarının zorlandığı durumlarda bile algoritma mevcut kapasiteyi en verimli şekilde kullanarak hatayı minimize etmiştir.

## 📂 Dosya Yapısı
* `main`: Yapılan kompanzasyon optimizasyonu projesi hakkında genel bilgilendirme (`readme.md`).
* `src/`: Kompanzasyon sisteminin optimizasyonunun yapıldığı matlab kodu (`haa_kompanzasyon.m`).
* `images/`: Simülasyon sonuçlarına ait grafikler (`Graph 1`, (`Graph 2`)).

---
*Bu proje TÜBİTAK 2209-A programı kapsamında hazırlanmıştır.
