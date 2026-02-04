# Case-4: High Supersonic Expansion & Performance Validation

## 1. Giriş ve Amaç
Bu rapor, lüle tasarımının **Case-4 (Durum 4)** koşullarındaki sayısal analiz sonuçlarını içermektedir. Bu aşamada, yüksek basınç farkı altında lülenin süpersonik deşarj kapasitesi ve elde edilen itki kuvvetinin teorik değerlerle doğrulanması amaçlanmıştır.

## 2. Geometrik Parametreler
Tasarımda kullanılan lüle geometrisi, yüksek genişleme oranına göre optimize edilmiştir:

* **Giriş Alanı ($A_7$):** $0.19635 \, m^2$
* **Boğaz Alanı ($A_8$):** $0.06709 \, m^2$
* **Alan Oranı ($A_9 / A_8$):** $2.000$
* **Çıkış Alanı ($A_9$):** $0.13418 \, m^2$
* **Yakınsaklık Yarım Açısı ($\alpha$):** $30^\circ$
* **Iraksaklık Yarım Açısı ($\theta$):** $12^\circ$

## 3. Sınır Koşulları (Boundary Conditions)
Analiz, ANSYS Fluent içerisinde aşağıdaki işletme koşulları altında gerçekleştirilmiştir. Akışkan olarak **İdeal Gaz** (Hava) seçilmiş olup, özgül ısı kapasitesi ($C_p$) sabit $1084.2 \, J/kgK$ kabul edilmiştir.

| Parametre | Sembol | Değer | Birim |
| :--- | :--- | :--- | :--- |
| Giriş Toplam Basıncı | $P_{t7}$ | 390,000 | Pa |
| Giriş Toplam Sıcaklığı | $T_{t7}$ | 792.16 | K |
| Ortam Basıncı | $P_0$ | 30,088 | Pa |
| Ortam Sıcaklığı | $T_0$ | 228.71 | K |

---

## 4. Performans Analizi ve Doğrulama

### 4.1. Kütlesel Debi Analizi ($\dot{m}$) ve Süreklilik Kontrolü
Süreklilik denkleminin sağlanması amacıyla hem giriş-çıkış farkı (sayısal kararlılık) hem de teorik değerle olan sapma (model doğruluğu) kontrol edilmiştir.

* **Teorik (Hedef) Debi:** $35.004 \, kg/s$
* **CFD Giriş Debisi ($\dot{m}_{in}$):** $35.20949 \, kg/s$
* **CFD Çıkış Debisi ($\dot{m}_{out}$):** $-35.20957 \, kg/s$

**1. Süreklilik Hatası (Giriş vs Çıkış):**

$$
\text{Hata}_{\text{süreklilik}} = \left| \frac{\dot{m}_{in} - |\dot{m}_{out}|}{\dot{m}_{in}} \right| \times 100 = \mathbf{\%0.0002}
$$

**2. Tahmin Hatası (CFD vs Teorik):**

$$
\text{Hata}_{\text{tahmin}} = \left| \frac{|\dot{m}_{out}| - 35.004}{35.004} \right| \times 100 = \mathbf{\%0.587}
$$

*%1'in altındaki bu sapma, çözüm ağının ve termodinamik modelin yüksek irtifa basınç koşullarında dahi mükemmel çalıştığını kanıtlamaktadır.*

### 4.2. Deşarj Katsayısı ($C_d$) Karşılaştırması
Boğaz bölgesindeki gerçek akışın ideal izentropik akışa oranı üzerinden hesaplanan $C_d$ analizi aşağıdadır:

$$
C_d = \frac{\dot{m}_{bulunan}}{\dot{m}_{ideal}} = \frac{35.20957}{37.199} = \mathbf{0.9465}
$$

* **Teorik $C_d$ Referansı:** $0.941$
* **CFD Hesaplanan $C_d$:** $0.9465$
* **Fark:** $\%0.58$

---

### 4.3. İtki Kuvveti ($F_g$) Analizi
Lüle çıkış yüzeyinden alınan verilerle toplam net itki hesaplanmıştır.

* **Çıkış Hızı ($V_9$):** $876.89 \, m/s$
* **Çıkış Mutlak Basıncı ($P_9$):** $35,660 \, Pa$
* **Çıkış Alanı ($A_9$):** $0.13418 \, m^2$

**İtki Formülü:**

$$
F_g = (\dot{m} \times V_9) + A_9 \times (P_9 - P_0)
$$

**CFD İtki Hesabı:**

$$
F_{g,CFD} = (35.20957 \times 876.89) + 0.13418 \times (35660 - 30088) = \mathbf{31.622 \, kN}
$$

---

### 4.4. İtki ($F_g$) ve Verim ($C_{fg}$) Karşılaştırmalı Analiz
Lülenin genel verimlilik göstergesi olan $C_{fg}$ değeri için kullanılan termodinamik denklemler aşağıdadır:

**İdeal Kütlesel Debi ve Çıkış Hızı Formülleri:**

$$
\dot{m}_{ideal} = \frac{A_8 \cdot P_{t7}}{\sqrt{T_{t7}}} \sqrt{\frac{\gamma}{R} \left( \frac{2}{\gamma+1} \right)^{\frac{\gamma+1}{\gamma-1}}} \quad , \quad V_{ideal} = \sqrt{2 \cdot C_p \cdot T_{t7} \left[ 1 - \left( \frac{P_0}{P_{t7}} \right)^{\frac{\gamma-1}{\gamma}} \right]}
$$

* **İdeal Kütlesel Debi ($\dot{m}_{ideal}$):** $37.199 \, kg/s$
* **İdeal Çıkış Hızı ($V_{ideal}$):** $944.24 \, m/s$
* **İdeal İtki ($F_{g,ideal}$):** $32.9398 \, kN$

**Karşılaştırma Tablosu:**

| Parametre | Teorik / Şartname | CFD Sonucu | Hata / Fark |
| :--- | :--- | :--- | :--- |
| **İtki Kuvveti ($F_g$)** | $30.99 \, kN$ | $31.622 \, kN$ | %2.04 |
| **İtki Katsayısı ($C_{fg}$)** | $0.966$ | $0.960$ | %0.62 |

**İtki Katsayısı ($C_{fg}$) Hesabı:**

$$
C_{fg,CFD} = \frac{31.622}{32.9398} = \mathbf{0.960}
$$

---

## 5. Sonuç ve Genel Değerlendirme

Case-4 analizleri sonucunda lüle, yüksek genişleme rejiminde (**Mach 2.55**) stabil ve yüksek verimli çalıştığını göstermiştir.

1. **Sayısal Doğrulama:** Süreklilik hatasının binde bir mertebesinin bile altında olması (**%0.0002**), çözümün mükemmel şekilde yakınsadığını ispatlar.
2. **Hassasiyet:** Basınç düzeltmesi sonrası verimlilik hatasının **%0.62**'ye düşmesi, analiz modelinin tasarım limitleri içindeki doğruluğunu kesinleştirmiştir.
3. **Performans:** Tasarlanan geometri, yüksek irtifa ve yüksek basınç oranlarında (High NPR) teorik itki değerlerini %98'in üzerinde bir tutarlılıkla üretmektedir.
4. **Verimlilik:** Hesaplanan **0.960** $C_{fg}$ değeri, süpersonik akıştaki sürtünme ve şok kayıplarının minimum düzeyde tutulduğunu doğrular.
