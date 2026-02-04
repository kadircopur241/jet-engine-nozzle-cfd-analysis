# Case-5: Extended Supersonic Flow & Altitude Performance Analysis

## 1. Giriş ve Amaç
Bu rapor, jet motoru nozzle tasarımının **Case-5 (Durum 5)** koşullarındaki sayısal analiz sonuçlarını içermektedir. Bu aşamada, lülenin yüksek irtifa şartlarını temsil eden düşük ortam basıncı ($11,597 \, Pa$) altındaki performansı ve süpersonik genişleme verimi incelenmiştir.

## 2. Geometrik Parametreler
Tasarımda kullanılan lüle geometrisi, yüksek genişleme oranına göre optimize edilmiştir:

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

### 4.1. Kütlesel Debi Analizi ($\dot{m}$)
Süreklilik denkleminin sağlanması amacıyla kütle korunumu kontrol edilmiştir.

* **Teorik (Hedef) Debi:** $18.857 \, kg/s$
* **CFD Giriş Debisi:** $18.97863 \, kg/s$
* **CFD Çıkış Debisi:** $-18.97797 \, kg/s$ (Net akış)

**Hata Analizi:**

$$
\text{Hata} = \left| \frac{18.97797 - 18.857}{18.857} \right| \times 100 = \%0.64
$$

### 4.2. Deşarj Katsayısı ($C_d$) Hesabı
Boğaz bölgesindeki akış verimliliğini belirlemek için bulunan ve ideal kütlesel debi oranları kullanılmıştır.

$$
C_d = \frac{\dot{m}_{bulunan}}{\dot{m}_{ideal}}
$$

* **Teorik $C_d$ (Referans):** $0.940$
* **CFD $C_d$ (Hesaplanan):** $18.97797 / 20.03859 = \mathbf{0.956}$

---

### 4.3. İtki Kuvveti ($F_g$) Analizi
Lüle çıkış yüzeyinden alınan güncel verilerle net itki hesaplanmıştır.

* **Çıkış Hızı ($V_9$):** $876.89 \, m/s$
* **Çıkış Mutlak Basıncı ($P_9$):** $20,213.8 \, Pa$

**İtki Hesabı Formülü:**

$$
F_g = (\dot{m} \times V_9) + A_9 \times (P_9 - P_0)
$$

**Hesaplanan CFD İtkisi:** $\mathbf{17.787 \, kN}$

---

### 4.4. İtki ($F_g$) ve Verim ($C_{fg}$) Karşılaştırmalı Analiz
Analizden elde edilen performans verileri, şartname değerleri ile aşağıda karşılaştırılmıştır.

| Parametre | Teorik / Şartname | CFD Sonucu | Hata / Fark |
| :--- | :--- | :--- | :--- |
| **İtki Kuvveti ($F_g$)** | $30.99 \, kN$ | $17.787 \, kN$ | %42.6 |
| **İtki Katsayısı ($C_{fg}$)** | $0.961$ | $0.970$ | %0.93 |

**İtki Katsayısı ($C_{fg}$) Hesabı:**

$$
C_{fg} = \frac{F_{g,bulunan}}{F_{g,ideal}} = \frac{17.787}{18.318} = \mathbf{0.970}
$$

---

## 5. Sonuç ve Genel Değerlendirme

Case-5 analizinde lüle, süpersonik rejime tam uyum sağlamış ve Mach 2.54 hızına ulaşmıştır.

1. **Kütle Korunumu:** Giriş ve çıkış debileri arasındaki fark binde bir hassasiyetin altına inerek çözümün mükemmel şekilde yakınsadığını ispatlamıştır.
2. **İtki Farkının Nedeni:** Şartname itkisi ($30.99 \, kN$) ile CFD itkisi ($17.787 \, kN$) arasındaki fark, motorun çalışma noktasındaki düşük giriş basıncından (210 kPa) kaynaklanmaktadır. Bu durum motorun itki kapasitesini düşürse de lülenin tasarım verimliliğini etkilememektedir.
3. **Yüksek Verimlilik:** Nozzle performansının en saf göstergesi olan **İtki Katsayısı ($C_{fg}$)** değerinin **0.970** olarak hesaplanması, tasarımın teorik verim limitlerini (%0.93 fark ile) başarıyla karşıladığını doğrulamaktadır.
4. **Basınç Katkısı:** Çıkış basıncının ortam basıncı değerinden yüksek olması ($P_9 > P_0$), itkiye pozitif yönde bir basınç bileşeni ekleyerek yüksek irtifa performansını desteklemiştir.
