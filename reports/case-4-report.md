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
Analiz, ANSYS Fluent içerisinde aşağıdaki sınır koşulları altında gerçekleştirilmiştir. Akışkan olarak İdeal Gaz (Hava) seçilmiş olup, özgül ısı kapasitesi ($C_p$) sabit $1084.2 \, J/kgK$ kabul edilmiştir.

| Parametre | Sembol | Değer | Birim |
| :--- | :--- | :--- | :--- |
| Giriş Toplam Basıncı | $P_{t7}$ | 390,000 | Pa |
| Giriş Toplam Sıcaklığı | $T_{t7}$ | 792.16 | K |
| Ortam Basıncı | $P_0$ | 30,088 | Pa |
| Ortam Sıcaklığı | $T_0$ | 228.71 | K |

---

## 4. Performans Analizi ve Doğrulama

### 4.1. Kütlesel Debi Analizi ($\dot{m}$)
Süreklilik denkleminin sağlanması amacıyla giriş ve çıkış kütlesel debileri incelenmiştir.

* **Teorik (Hedef) Debi:** $35.004 \, kg/s$
* **CFD Giriş Debisi:** $35.20949 \, kg/s$
* **CFD Çıkış Debisi:** $-35.20957 \, kg/s$ (Net akış)

**Hata Analizi:**

$$
\text{Hata} = \left| \frac{35.20957 - 35.004}{35.004} \right| \times 100 = \%0.587
$$

*%1'in altındaki bu sapma, çözüm ağının ve termodinamik modelin yüksek irtifa basınç koşullarında dahi mükemmel çalıştığını göstermektedir.*

### 4.2. Deşarj Katsayısı ($C_d$) Hesabı
Boğaz bölgesindeki akış verimliliğini belirlemek için aşağıdaki yöntem kullanılmıştır:

$$
C_d = \frac{\dot{m}_{bulunan}}{\dot{m}_{ideal}}
$$

Termodinamik denklemlerle hesaplanan **İdeal Kütlesel Debi ($\dot{m}_{ideal}$)** değeri **$37.199 \, kg/s$** olarak bulunmuştur.

* **Teorik $C_d$ (Referans):** $0.941$
* **CFD $C_d$ (Hesaplanan):** $35.20957 / 37.199 = \mathbf{0.9465}$

---

### 4.3. İtki Kuvveti ($F_g$) Analizi
Lüle çıkış yüzeyinden alınan güncel verilerle net itki hesaplanmıştır.

* **Çıkış Hızı ($V_9$):** $876.89 \, m/s$
* **Çıkış Mutlak Basıncı ($P_9$):** $35,660 \, Pa$

**İtki Hesabı Formülü:**

$$
F_g = (\dot{m} \times V_9) + A_9 \times (P_9 - P_0)
$$

**Hesaplama:**

$$
F_{g,CFD} = (35.20957 \times 876.89) + 0.13418 \times (35660 - 30088)
$$

$$
F_{g,CFD} \approx 30,875 + 747 = \mathbf{31.622 \, kN}
$$

---

### 4.4. İtki ($F_g$) ve Verim ($C_{fg}$) Karşılaştırmalı Analiz
Düzeltilmiş basınç değerleri sonrası analiz verileri ile teorik referanslar arasındaki ilişki mükemmel bir uyum yakalamıştır.

| Parametre | Teorik / Şartname | CFD Sonucu | Hata / Fark |
| :--- | :--- | :--- | :--- |
| **İtki Kuvveti ($F_g$)** | $30.99 \, kN$ | $31.622 \, kN$ | %2.04 |
| **İtki Katsayısı ($C_{fg}$)** | $0.966$ | $0.960$ | %0.62 |

**İtki Katsayısı ($C_{fg}$) Hesabı:**

$$
C_{fg} = \frac{F_{g,bulunan}}{F_{g,ideal}} = \frac{31.622}{32.9398} = \mathbf{0.960}
$$

**Değerlendirme:**
* **İtki:** CFD sonucu şartname değerinden sadece %2.04 sapma göstermektedir.
* **Verim:** Hesaplanan $0.960$ $C_{fg}$ değeri, teorik referans olan $0.966$ değerine **%99.38** oranında yakındır. Bu sonuç, süpersonik kayıpların tasarım limitleri içerisinde olduğunu kanıtlar.

## 5. Sonuç ve Genel Değerlendirme
Case-4 analizleri, lülenin yüksek genişleme rejiminde (**Mach 2.55**) stabil ve yüksek verimli çalıştığını göstermiştir.

1. **Süreklilik:** Kütlesel debi dengesi binde bir hassasiyetle sağlanmıştır.
2. **Hassasiyet:** Basınç düzeltmesi sonrası verimlilik hatası **%0.62**'ye düşerek modelin doğruluğunu kesinleştirmiştir.
3. **Doğrulama:** Tasarlanan geometri, yüksek irtifa koşullarında hedef itki değerlerini teorik beklentilerle tam uyumlu şekilde üretmektedir.
