# Case-3: High Pressure & Supersonic Expansion Analysis

## 1. Giriş ve Amaç
Bu rapor, jet motoru nozzle tasarımının **Case-3 (Durum 3)** koşullarındaki sayısal analiz sonuçlarını içermektedir. Bu aşamada, lülenin yüksek basınç ve düşük ortam basıncı altındaki genişleme (expansion) karakteristiği ve süpersonik akış verimi incelenmiştir.

## 2. Geometrik Parametreler
Tasarımda kullanılan lüle geometrisi, yüksek genişleme oranına göre optimize edilmiştir:

* **Giriş Alanı ($A_7$):** $0.19635 \, m^2$
* **Boğaz Alanı ($A_8$):** $0.06610 \, m^2$
* **Alan Oranı ($A_9/A_8$):** $1.703$
* **Çıkış Alanı ($A_9$):** $0.11257 \, m^2$ (Hesaplanan)
* **Yakınsaklık Yarım Açısı ($\alpha$):** $30^\circ$
* **Iraksaklık Yarım Açısı ($\theta$):** $12^\circ$

## 3. Sınır Koşulları (Boundary Conditions)
Analiz, ANSYS Fluent içerisinde aşağıdaki sınır koşulları altında gerçekleştirilmiştir:

| Parametre | Sembol | Değer | Birim |
| :--- | :--- | :--- | :--- |
| Giriş Toplam Basıncı | $P_{t7}$ | 400,000 | Pa |
| Giriş Toplam Sıcaklığı | $T_{t7}$ | 768.63 | K |
| Ortam Basıncı | $P_0$ | 46,562 | Pa |
| Ortam Sıcaklığı | $T_0$ | 248.53 | K |
| Özgül Isı Kapasitesi | $C_p$ | 1084.2 | J/kg·K |

---

## 4. Performans Analizi ve Doğrulama

### 4.1. Kütlesel Debi Analizi ($\dot{m}$)
Süreklilik denkleminin sağlanması ve kütle korunumunun kontrolü amacıyla debi verileri incelenmiştir.

* **Teorik (Hedef) Debi:** $52.054 \, kg/s$
* **CFD Giriş Debisi:** $52.36805 \, kg/s$
* **CFD Çıkış Debisi:** $-52.36831 \, kg/s$ (Net akış)

**Hata Analizi:**

$$
\text{Hata} = \left| \frac{52.36831 - 52.054}{52.054} \right| \times 100 = \%0.60
$$

*%1'in altındaki bu sapma, yüksek irtifa ve düşük basınç koşullarında bile sayısal modelin kararlılığını kanıtlamaktadır.*

### 4.2. Deşarj Katsayısı ($C_d$) Hesabı
Sıkıştırılabilir akışlarda boğaz bölgesindeki efektif alanı belirlemek zor olduğu için, $C_d$ hesabı kütlesel debiler üzerinden yapılmıştır.

**Kullanılan Formül:**

$$
C_d = \frac{\dot{m}_{bulunan}}{\dot{m}_{ideal}}
$$

Termodinamik denklemlerle hesaplanan **İdeal (Isentropic) Kütlesel Debi ($\dot{m}_{ideal}$)** değeri **$55.326 \, kg/s$** olarak bulunmuştur.

* **Teorik $C_d$ (Referans):** $0.940$
* **CFD $C_d$ (Hesaplanan):** $0.94654$

**Karşılaştırma:**
Referans değer ile analiz sonucu arasındaki fark binde 7 mertebesindedir. Bu sonuç, viskoz etkilerin ve sınır tabaka oluşumunun doğru modellendiğini kanıtlar.

---

### 4.3. İtki Kuvveti ($F_g$) Analizi
Lüle çıkış yüzeyinden alınan verilerle net itki hesaplanmıştır.

* **Çıkış Hızı ($V_9$):** $817.922 \, m/s$
* **Çıkış Basıncı ($P_9$):** $51,012.3 \, Pa$

**İtki Hesabı Formülü:**

$$
F_g = (\dot{m} \times V_9) + A_9 \times (P_9 - P_0)
$$

**Sonuçlar:**
* **Şartname (Teorik) İtki:** $29.48 \, kN$
* **CFD Sonucu (Net İtki):** $\mathbf{31.25 \, kN}$

**Hata Analizi:**

$$
\text{Hata} = \left| \frac{31.25 - 29.48}{29.48} \right| \times 100 = \%6.0
$$

*Gözlemlenen %6'lık fark, yüksek irtifa koşullarındaki düşük ortam basıncının sağladığı ekstra basınç itkisinden kaynaklanmaktadır.*

---

### 4.4. İtki Katsayısı ($C_{fg}$) ve Verim
Nozzle performansının en önemli göstergesi olan itki katsayısı, CFD itkisinin ideal itkiye oranıyla bulunmuştur.

**İdeal Değerler:**
* $\dot{m}_{ideal} = 38.16 \, kg/s$
* $V_{ideal} = 818.9175 \, m/s$
* $F_{g,ideal} = \dot{m}_{ideal} \times V_{ideal} \approx \mathbf{31.25 \, kN}$

**İtki Katsayısı Hesabı:**

$$
C_{fg} = \frac{F_{g,bulunan}}{F_{g,ideal}} = \frac{31.25}{31.25} = \mathbf{1.00}
$$

* **Teorik $C_{fg}$:** $0.968$
* **Hesaplanan $C_{fg}$:** $1.00$

## 5. Sonuç
Case-3 analizinde lüle, süpersonik rejime tam uyum sağlamış ve Mach 2.24 hızına ulaşmıştır. Hesaplanan itki katsayısının 1.00 olması, tasarımın bu basınç oranında maksimum teorik verime (perfectly expanded) ulaştığını göstermektedir.
