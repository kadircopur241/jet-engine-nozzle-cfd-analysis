# Case-7: Transonic Flow & Pressure Recovery Analysis

## 1. Giriş ve Amaç
Bu rapor, jet motoru nozzle tasarımının **Durum 7 (Case-7)** koşullarındaki sayısal analiz sonuçlarını içermektedir. Bu aşamada, lülenin orta irtifa şartlarını temsil eden basınç değerleri altındaki performansı, süreklilik denklemi doğrulaması ve itki verimi incelenmiştir.

## 2. Geometrik Parametreler
Tasarımda kullanılan lüle geometrisi, belirli bir genişleme oranına ($A_9/A_8 = 1.159$) göre optimize edilmiştir:

* **Giriş Alanı ($A_7$):** $0.19635 \, m^2$
* **Boğaz Alanı ($A_8$):** $0.09189 \, m^2$
* **Alan Oranı ($A_9 / A_8$):** $1.159$
* **Yakınsaklık Yarım Açısı ($\alpha$):** $30^\circ$
* **Iraksaklık Yarım Açısı ($\theta$):** $12^\circ$

## 3. Sınır Koşulları (Boundary Conditions)
Analiz, ANSYS Fluent içerisinde aşağıdaki işletme koşulları altında gerçekleştirilmiştir. Akışkan olarak "İdeal Gaz" seçilmiş ve özgül ısı kapasitesi ($C_p$) $1022.897 \, J/kgK$ olarak tanımlanmıştır.

| Parametre | Sembol | Değer | Birim |
| :--- | :--- | :--- | :--- |
| Giriş Toplam Basıncı | $P_{t7}$ | 150,000 | Pa |
| Giriş Toplam Sıcaklığı | $T_{t7}$ | 470.59 | K |
| Ortam Basıncı | $P_0$ | 37,599 | Pa |
| Ortam Sıcaklığı | $T_0$ | 238.62 | K |
| Özgül Isı Kapasitesi | $C_p$ | 1022.897 | J/kgK |

---

## 4. Performans Analizi ve Doğrulama

### 4.1. Kütlesel Debi Analizi ($\dot{m}$)
Süreklilik denkleminin sağlanması amacıyla kütle korunumu kontrol edilmiş ve teorik değerle kıyaslanmıştır.

* **Teorik (Hedef) Debi:** $24.503 \, kg/s$
* **CFD Giriş Debisi:** $24.41262 \, kg/s$
* **CFD Çıkış Debisi:** $-24.41219 \, kg/s$

**1. Süreklilik Hata Oranı / Fark (Giriş vs Çıkış):**

$$\text{Hata}_{\text{süreklilik}} = \left| \frac{\dot{m}_{in} - |\dot{m}_{out}|}{\dot{m}_{in}} \right| \times 100 = \%0.0018$$

**2. Tahmin Hata Oranı / Fark (CFD vs Teorik):**

$$\text{Hata}_{\text{tahmin}} = \left| \frac{|\dot{m}_{out}| - 24.503}{24.503} \right| \times 100 = \%0.37$$

### 4.2. Deşarj Katsayısı ($C_d$) Hesabı
Boğaz bölgesindeki akış verimliliğini belirlemek için analizden elde edilen debinin ideal debiye oranı kullanılmıştır.

$$C_d = \frac{\dot{m}_{bulunan}}{\dot{m}_{ideal}}$$

* **Teorik $C_d$ (Referans):** $0.956$
* **CFD $C_d$ (Hesaplanan):** **0.9529**

### 4.3. İtki Kuvveti ($F_g$) Analizi
Lüle çıkış yüzeyinden alınan verilerle toplam net itki hesaplanmıştır.

* **Çıkış Hızı ($V_9$):** $517.54 \, m/s$
* **Çıkış Mutlak Basıncı ($P_9$):** $44,592.1 \, Pa$
* **Çıkış Alanı ($A_9$):** $0.1065 \, m^2$

**İtki Formülü:**

$$F_g = (\dot{m} \times V_9) + A_9 \times (P_9 - P_0)$$

**CFD İtki Hesabı:**

$$F_{g,CFD} = (24.41219 \times 517.54) + 0.1065 \times (44592.1 - 37599) = 13.38 \, kN$$

### 4.4. İtki ($F_g$) ve Verim ($C_{fg}$) Karşılaştırmalı Analiz
İdeal değerler için kullanılan isentropik termodinamik denklemler aşağıdadır:

**İdeal Kütlesel Debi ve Çıkış Hızı Formülleri:**

$$\dot{m}_{ideal} = \frac{P_{t7} A_8}{\sqrt{T_{t7}}} \sqrt{\frac{\gamma}{R} \left( \frac{2}{\gamma+1} \right)^{\frac{\gamma+1}{\gamma-1}}}$$

$$V_{ideal} = \sqrt{2 \cdot C_p \cdot T_{t7} \left[ 1 - \left( \frac{P_0}{P_{t7}} \right)^{\frac{\gamma-1}{\gamma}} \right]}$$

* **İdeal Kütlesel Debi ($\dot{m}_{ideal}$):** $25.6178 \, kg/s$
* **İdeal Çıkış Hızı ($V_{ideal}$):** $551.68 \, m/s$
* **İdeal İtki ($F_{g,ideal}$):** $14.132 \, kN$

**Karşılaştırma Tablosu:**

| Parametre | Teorik / Şartname | CFD Sonucu | Hata / Fark |
| :--- | :--- | :--- | :--- |
| **İtki Kuvveti ($F_g$)** | $13.22 \, kN$ | $13.38 \, kN$ | %1.21 |
| **İtki Katsayısı ($C_{fg}$)** | $0.970$ | **0.947** | %2.37 |

---

## 5. Sonuç ve Genel Değerlendirme

Case-7 analizinde lüle, transonik geçişi başarıyla tamamlamış ve süpersonik rejime girmiştir. Yapılan analizler sonucunda şu çıkarımlar yapılmıştır:

1. **Sayısal Doğrulama:** Kütlesel debi tahmin hata oranının **%0.37** gibi çok düşük bir seviyede kalması, çözümün yüksek hassasiyetle yakınsadığını kanıtlamıştır.
2. **Katsayı Uyumu:** Hesaplanan akış katsayısının ($C_d = 0.9529$) teorik referansla (0.956) tam uyum göstermesi, boğaz bölgesindeki daralma etkilerinin doğru modellendiğini ispatlar.
3. **İtki Performansı:** Hesaplanan itki (13.38 kN) ile teorik itki (13.22 kN) arasındaki farkın minimal olması, lülenin momentum üretim kapasitesinin beklentileri karşıladığını gösterir.
4. **Görsel Analiz:** Mach sayısı konturları, akışun boğazda sonik hıza ulaştığını; basınç konturları ise çıkışta ortam basıncıyla olan farkın ($P_9 > P_0$) itkiye pozitif katkı sağladığını doğrulamaktadır.
   
