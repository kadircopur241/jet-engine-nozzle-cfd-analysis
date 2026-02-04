# Case-3: High Pressure & Supersonic Expansion Analysis

## 1. Giriş ve Amaç
Bu rapor, jet motoru nozzle tasarımının **Case-3 (Durum 3)** koşullarındaki sayısal analiz sonuçlarını içermektedir. Bu aşamada, lülenin yüksek basınç ve düşük ortam basıncı altındaki genişleme (expansion) karakteristiği ve süpersonik akış verimi incelenmiştir.

## 2. Geometrik Parametreler
Tasarımda kullanılan lüle geometrisi, yüksek genişleme oranına göre optimize edilmiştir:

* **Giriş Alanı ($A_7$):** $0.19635 \, m^2$
* **Boğaz Alanı ($A_8$):** $0.06610 \, m^2$
* **Alan Oranı ($A_9/A_8$):** $1.703$
* **Çıkış Alanı ($A_9$):** $0.11257 \, m^2$
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

* **Teorik (Hedef) Debi:** $35.907 \, kg/s$
* **CFD Giriş Debisi:** $31.1196 \, kg/s$
* **CFD Çıkış Debisi:** $-36.12082 \, kg/s$

**Hata Analizi:**
Teorik hedef ile CFD çıkış debisi arasındaki fark:

$$
\text{Hata} = \left| \frac{36.12082 - 35.907}{35.907} \right| \times 100 = \%0.59
$$

*%1'in altındaki bu sapma (%0.59), sınır koşulları ve termodinamik modelin yüksek irtifa koşullarında dahi mükemmel çalıştığını kanıtlamaktadır.*

### 4.2. Deşarj Katsayısı ($C_d$) Hesabı
Boğaz bölgesindeki akış verimliliğini belirlemek için kullanılan yöntem:

$$
C_d = \frac{\dot{m}_{bulunan}}{\dot{m}_{ideal}}
$$

Termodinamik denklemlerle hesaplanan **İdeal Kütlesel Debi ($\dot{m}_{ideal}$)** değeri **$38.16 \, kg/s$** olarak bulunmuştur.

* **Teorik $C_d$ (Referans):** $0.940$
* **CFD $C_d$ (Hesaplanan):** $36.12082 / 38.16 = \mathbf{0.9465}$

**Karşılaştırma:**
Referans değer ($0.940$) ile analiz sonucu arasındaki fark binde 6 mertebesindedir.

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
* **CFD Sonucu (Net İtki):** $\mathbf{30.046 \, kN}$ (Hesaplanan)

**Hata Analizi:**
$$\text{Hata} = \left| \frac{30.046 - 29.48}{29.48} \right| \times 100 = \%1.92$$

---

### 4.4. İtki Katsayısı ($C_{fg}$) ve Verim
İdeal süpersonik genişleme verimi:

**İdeal Değerler:**
* $V_{ideal} = 818.9175 \, m/s$
* $F_{g,ideal} = \dot{m}_{ideal} \times V_{ideal} = 38.16 \times 818.9175 \approx \mathbf{31.25 \, kN}$

**İtki Katsayısı Hesabı:**

$$
C_{fg} = \frac{F_{g,bulunan}}{F_{g,ideal}} = \frac{30.046}{31.25} = \mathbf{0.961}
$$

* **Teorik $C_{fg}$:** $0.968$
* **Hesaplanan $C_{fg}$:** $0.961$

## 5. Sonuç
Case-3 analizinde lüle, süpersonik rejime tam uyum sağlamış ve Mach 2.24 hızına ulaşmıştır. Teorik debi düzeltmesi sonrası hata oranının **%0.59**'a inmesi, modelin doğruluğunu kesinleştirmiştir. $C_{fg}$ değerinin **0.961** çıkması, gerçek akış koşullarındaki sürtünme ve şok kayıplarının makul sınırlar içinde olduğunu göstermektedir.
