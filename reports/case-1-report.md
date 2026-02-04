# Case-1: Design Point (DP) Analysis & Validation Report

## 1. Giriş ve Amaç
Bu rapor, tasarlanan Yakınsak-Iraksak (CD) lülenin **Design Point (DP)** koşullarındaki aerodinamik performansını doğrulamak amacıyla hazırlanmıştır. Analiz sonuçları (CFD), teorik termodinamik hesaplamalar ve tasarım şartnamesi verileri ile karşılaştırılarak sayısal modelin doğruluğu test edilmiştir.

## 2. Geometrik Parametreler
Lüle tasarımında akış ayrılmalarını önlemek ve optimum genişlemeyi sağlamak amacıyla aşağıdaki geometrik kabuller yapılmıştır:

* **Giriş Alanı ($A_7$):** $0.19632 \, m^2$
* **Boğaz Alanı ($A_8$):** $0.06745 \, m^2$
* **Alan Oranı ($A_9/A_8$):** $1.178$
* **Çıkış Alanı ($A_9$):** $0.07945 \, m^2$
* **Yakınsaklık Yarım Açısı ($\alpha$):** $30^\circ$
* **Iraksaklık Yarım Açısı ($\theta$):** $12^\circ$

## 3. Sınır Koşulları (Boundary Conditions)
Analiz, ANSYS Fluent içerisinde aşağıdaki işletme koşulları altında gerçekleştirilmiştir. Akışkan olarak **İdeal Gaz** (Hava) seçilmiş olup, özgül ısı kapasitesi ($C_p$) sabit $1084.2 \, J/kgK$ kabul edilmiştir.

| Parametre | Sembol | Değer | Birim |
| :--- | :--- | :--- | :--- |
| Giriş Toplam Basıncı | $P_{t7}$ | 420,000 | Pa |
| Giriş Toplam Sıcaklığı | $T_{t7}$ | 800 | K |
| Ortam Basıncı | $P_0$ | 101,325 | Pa |
| Ortam Sıcaklığı | $T_0$ | 288.15 | K |

---

## 4. Performans Analizi ve Doğrulama

### 4.1. Kütlesel Debi Analizi ($\dot{m}$)
Süreklilik denkleminin sağlanması ve kütle korunumunun kontrolü amacıyla giriş ve çıkış debileri incelenmiştir.

* **Teorik (Hedef) Debi:** $37.714 \, kg/s$
* **CFD Giriş Debisi:** $38.014 \, kg/s$
* **CFD Çıkış Debisi:** $-38.012 \, kg/s$

**Hata Analizi:**

$$
\text{Hata} = \left| \frac{38.012 - 37.714}{37.714} \right| \times 100 = \mathbf{\%0.79}
$$

*%1'in altındaki bu sapma, çözüm ağının ve sınır koşullarının yüksek doğruluğunu göstermektedir.*

### 4.2. Deşarj Katsayısı ($C_d$) Hesabı
Boğaz bölgesindeki akış verimliliğini belirlemek için bulunan kütlesel debinin ideal izentropik debiye oranı kullanılmıştır.

$$
C_d = \frac{\dot{m}_{bulunan}}{\dot{m}_{ideal}}
$$

* **Teorik $C_d$ (Referans):** $0.941$
* **CFD $C_d$ (Hesaplanan):** $38.012 / 40.07 = \mathbf{0.9485}$

---

### 4.3. İtki Kuvveti ($F_g$) Analizi
Lüle çıkış yüzeyinden alınan verilerle toplam net itki hesaplanmıştır.

* **Çıkış Hızı ($V_9$):** $686.264 \, m/s$
* **Çıkış Mutlak Basıncı ($P_9$):** $119,938.5 \, Pa$
* **Çıkış Alanı ($A_9$):** $0.07945 \, m^2$

**İtki Formülü:**

$$
F_g = (\dot{m} \times V_9) + A_9 \times (P_9 - P_0)
$$

**CFD İtki Hesabı:**

$$
F_{g,CFD} = (38.012 \times 686.264) + 0.07945 \times (119938.5 - 101325) = \mathbf{27.56 \, kN}
$$

---

### 4.4. İtki ($F_g$) ve Verim ($C_{fg}$) Karşılaştırmalı Analiz
Lülenin genel verimlilik göstergesi olan $C_{fg}$ değeri için kullanılan termodinamik denklemler aşağıdadır:

**İdeal Kütlesel Debi ve Çıkış Hızı Formülleri:**

$$                                                                                                                                                 
\dot{m}_{ideal} = \frac{A_8 \cdot P_{t7}}{\sqrt{T_{t7}}} \sqrt{\frac{\gamma}{R} \left( \frac{2}{\gamma+1} \right)^{\frac{\gamma+1}{\gamma-1}}},    V_{ideal} = \sqrt{2 \cdot C_p \cdot T_{t7} \left[ 1 - \left( \frac{P_0}{P_{t7}} \right)^{\frac{\gamma-1}{\gamma}} \right]}
$$                                                                                                                                                 


* **İdeal Kütlesel Debi ($\dot{m}_{ideal}$):** $40.07 \, kg/s$
* **İdeal Çıkış Hızı ($V_{ideal}$):** $710.193 \, m/s$
* **İdeal İtki ($F_{g,ideal}$):** $28.46 \, kN$

**Karşılaştırma Tablosu:**

| Parametre | Teorik / Şartname | CFD Sonucu | Hata / Fark |
| :--- | :--- | :--- | :--- |
| **İtki Kuvveti ($F_g$)** | $26.98 \, kN$ | $27.56 \, kN$ | %2.1 |
| **İtki Katsayısı ($C_{fg}$)** | $0.970$ | $0.968$ | %0.2 |

**İtki Katsayısı ($C_{fg}$) Hesabı:**

$$
C_{fg,CFD} = \frac{27.56}{28.46} = \mathbf{0.968}
$$

---

## 5. Sonuç ve Genel Değerlendirme

Case-1 (DP) analizi sonucunda elde edilen veriler ışığında şu çıkarımlar yapılmıştır:

1. **Sayısal Kararlılık:** Giren ve çıkan kütlesel debi farkı binde bir mertebesindedir. Bu durum, CFD çözümünün mükemmel şekilde yakınsadığını ispatlamıştır.
2. **Kütlesel Debi Doğrulaması:** Analizden elde edilen kütlesel debinin hedef değerle olan **%0.79**'luk farkı, sayısal modelin güvenilirliğini kanıtlar.
3. **İtki Performansı:** Elde edilen **27.56 kN** itki kuvveti, tasarım hedefi olan 26.98 kN ile yüksek uyum içindedir.
4. **Verimlilik:** Hesaplanan **0.968** $C_{fg}$ değeri, tasarımın standart koşullarda %96.8 verimle çalıştığını ve teorik beklentileri tam tutarlılıkla karşıladığını göstermektedir.
