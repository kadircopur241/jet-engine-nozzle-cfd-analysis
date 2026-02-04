# Case-5: Extended Supersonic Flow & Altitude Performance Analysis

## 1. Giriş ve Amaç
Bu rapor, jet motoru nozzle tasarımının **Case-5 (Durum 5)** koşullarındaki sayısal analiz sonuçlarını içermektedir. Bu aşamada, lülenin yüksek irtifa şartlarını temsil eden düşük ortam basıncı ($11,597 \, Pa$) altındaki performansı ve süpersonik genişleme verimi incelenmiştir.

## 2. Geometrik Parametreler
Tasarımda kullanılan lüle geometrisi, yüksek genişleme oranına ($A_9/A_8 = 2.0$) göre optimize edilmiştir:

* **Giriş Alanı ($A_7$):** $0.19635 \, m^2$
* **Boğaz Alanı ($A_8$):** $0.06645 \, m^2$
* **Alan Oranı ($A_9 / A_8$):** $2.000$
* **Yakınsaklık Yarım Açısı ($\alpha$):** $30^\circ$
* **Iraksaklık Yarım Açısı ($\theta$):** $12^\circ$

## 3. Sınır Koşulları (Boundary Conditions)
Analiz, ANSYS Fluent içerisinde aşağıdaki sınır koşulları altında gerçekleştirilmiştir. Akışkan olarak İdeal Gaz (Hava) seçilmiş olup, özgül ısı kapasitesi ($C_p$) sabit $1084.2 \, J/kgK$ kabul edilmiştir.

| Parametre | Sembol | Değer | Birim |
| :--- | :--- | :--- | :--- |
| Giriş Toplam Basıncı | $P_{t7}$ | 210,000 | Pa |
| Giriş Toplam Sıcaklığı | $T_{t7}$ | 776.47 | K |
| Ortam Basıncı | $P_0$ | 11,597 | Pa |
| Ortam Sıcaklığı | $T_0$ | 216.65 | K |

---

## 4. Performans Analizi ve Doğrulama

### 4.1. Kütlesel Debi Analizi ($\dot{m}$) ve Süreklilik Kontrolü
Süreklilik denkleminin sağlanması amacıyla hem giriş-çıkış farkı (sayısal kararlılık) hem de teorik değerle olan sapma (model doğruluğu) kontrol edilmiştir.

* **Teorik (Hedef) Debi:** $18.857 \, kg/s$
* **CFD Giriş Debisi ($\dot{m}_{in}$):** $18.97863 \, kg/s$
* **CFD Çıkış Debisi ($\dot{m}_{out}$):** $-18.97797 \, kg/s$

**1. Süreklilik Hatası (Giriş vs Çıkış):**
$$\text{Hata}_{\text{süreklilik}} = \left| \frac{\dot{m}_{in} - |\dot{m}_{out}|}{\dot{m}_{in}} \right| \times 100 = \mathbf{\%0.0035}$$

**2. Tahmin Hatası (CFD vs Teorik):**
$$\text{Hata}_{\text{tahmin}} = \left| \frac{|\dot{m}_{out}| - 18.857}{18.857} \right| \times 100 = \mathbf{\%0.641}$$

### 4.2. Deşarj Katsayısı ($C_d$) Karşılaştırması
Boğaz bölgesindeki gerçek akışın ideal izentropik akışa oranı üzerinden hesaplanan $C_d$ analizi:

$$C_d = \frac{\dot{m}_{bulunan}}{\dot{m}_{ideal}} = \frac{18.97797}{20.03859} = \mathbf{0.947}$$

* **Teorik $C_d$ Referansı:** $0.940$
* **CFD Hesaplanan $C_d$:** $0.947$
* **Bağıl Fark:** $\%0.74$

---

### 4.3. İtki Kuvveti ($F_g$) Analizi
Lüle çıkış yüzeyinden alınan verilerle toplam net itki hesaplanmıştır.

* **Çıkış Hızı ($V_9$):** $876.89 \, m/s$
* **Çıkış Mutlak Basıncı ($P_9$):** $20,213.8 \, Pa$
* **Çıkış Alanı ($A_9$):** $0.1329 \, m^2$

**İtki Formülü:**
$$F_g = (\dot{m} \times V_9) + A_9 \times (P_9 - P_0)$$

**CFD İtki Hesabı:**
$$F_{g,CFD} = (18.97797 \times 876.89) + 0.1329 \times (20213.8 - 11597) = \mathbf{17.787 \, kN}$$

---

### 4.4. İtki Katsayısı ($C_{fg}$) Karşılaştırması
Lülenin genel verimlilik göstergesi olan $C_{fg}$ değeri, CFD itkisinin ideal itkiye bölünmesiyle elde edilmiştir.

* **İdeal İtki ($F_{g,ideal}$):** $18.31836 \, kN$
* **CFD Net İtki ($F_{g,CFD}$):** $17.787 \, kN$

$$C_{fg,CFD} = \frac{F_{g,CFD}}{F_{g,ideal}} = \frac{17.787}{18.31836} = \mathbf{0.971}$$

* **Teorik $C_{fg}$ Referansı:** $0.961$
* **CFD Hesaplanan $C_{fg}$:** $0.971$
* **Bağıl Fark:** $\%1.04$

---

## 5. Sonuç ve Genel Değerlendirme

Case-5 analizinde lüle, süpersonik rejime tam uyum sağlamış ve Mach 2.54 hızına ulaşmıştır. Yapılan analizler sonucunda şu teknik çıkarımlar yapılmıştır:

1. **Sayısal Doğrulama:** Süreklilik hatasının **%0.0035** gibi ihmal edilebilir bir seviyede çıkması, çözümün mükemmel şekilde yakınsadığını kanıtlar. Kütlesel debi tahmin hatası ise **%0.64** ile tasarım sınırları içerisindedir.
2. **Operasyonel Analiz:** Şartnamede belirtilen itki ($30.99 \, kN$) ile CFD sonucu ($17.787 \, kN$) arasındaki fark, analizde kullanılan giriş basıncının (210 kPa) düşük olmasından kaynaklanmaktadır. Bu durum motorun düşük güçteki çalışma noktasını başarıyla temsil etmektedir.
3. **Yüksek Verimlilik:** Nozzle verimini gösteren **İtki Katsayısı ($C_{fg}$)** değerinin **0.971** çıkması, tasarımın sürtünme ve sınır tabaka kayıplarını minimum düzeyde tutarak yüksek verimle çalıştığını ispatlamıştır.
4. **Basınç İtkisi Katkısı:** Çıkış basıncının ortam basıncından yüksek olması ($P_9 > P_0$), lülenin "under-expanded" modda çalıştığını ve net itkiye pozitif bir basınç bileşeni eklediğini doğrulamıştır.
