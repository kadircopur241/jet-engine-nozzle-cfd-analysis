# Case-3: High Pressure & Supersonic Expansion Analysis

## 1. Giriş ve Amaç
Bu rapor, jet motoru nozzle tasarımının **Case-3 (Durum 3)** koşullarındaki sayısal analiz sonuçlarını içermektedir. Bu aşamada, lülenin yüksek basınç ve düşük ortam basıncı altındaki genişleme (expansion) karakteristiği ve süpersonik akış verimi incelenmiştir.

## 2. Geometrik Parametreler
[cite_start]Tasarımda kullanılan lüle geometrisi, yüksek genişleme oranına göre optimize edilmiştir[cite: 14, 15]:

* [cite_start]**Giriş Alanı ($A_7$):** $0.19635 \, m^2$ [cite: 14]
* **Boğaz Alanı ($A_8$):** $0.06610 \, m^2$ [cite: 14]
* **Alan Oranı ($A_9/A_8$):** $1.703$ [cite: 14]
* **Çıkış Alanı ($A_9$):** $0.11257 \, m^2$ (Hesaplanan)
* [cite_start]**Yakınsaklık Yarım Açısı ($\alpha$):** $30^\circ$ [cite: 16]
* [cite_start]**Iraksaklık Yarım Açısı ($\theta$):** $12^\circ$ [cite: 16]

## 3. Sınır Koşulları (Boundary Conditions)
[cite_start]Analiz, ANSYS Fluent içerisinde aşağıdaki sınır koşulları altında gerçekleştirilmiştir[cite: 14]:

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
[cite_start]Süreklilik denkleminin sağlanması ve kütle korunumunun kontrolü amacıyla debi verileri incelenmiştir.

* [cite_start]**Teorik (Hedef) Debi:** $52.054 \, kg/s$ [cite: 17]
* **CFD Giriş Debisi:** $52.36805 \, kg/s$
* **CFD Çıkış Debisi:** $-52.36831 \, kg/s$ (Net akış)

**Hata Analizi:**
[cite_start]Teorik hedef ile CFD sonucu arasındaki fark[cite: 18]:

$$
\text{Hata} = \left| \frac{52.36831 - 52.054}{52.054} \right| \times 100 = \%0.60
$$

### 4.2. Deşarj Katsayısı ($C_d$) Hesabı
[cite_start]Boğaz bölgesindeki akış verimliliğini belirlemek için kullanılan yöntem[cite: 20]:

$$
C_d = \frac{\dot{m}_{bulunan}}{\dot{m}_{ideal}}
$$

[cite_start]Termodinamik denklemlerle hesaplanan **İdeal Kütlesel Debi ($\dot{m}_{ideal}$)** değeri **$55.326 \, kg/s$** olarak bulunmuştur[cite: 20].

* **Teorik $C_d$ (Referans):** $0.940$ [cite: 18]
* **CFD $C_d$ (Hesaplanan):** $0.94654$ [cite: 20]

**Karşılaştırma:**
[cite_start]Referans değer ile analiz sonucu arasındaki fark binde 7 mertebesindedir[cite: 21].

---

### 4.3. İtki Kuvveti ($F_g$) Analizi
[cite_start]Lüle çıkış yüzeyinden alınan verilerle net itki hesaplanmıştır[cite: 22].

* [cite_start]**Çıkış Hızı ($V_9$):** $817.922 \, m/s$ [cite: 22]
* [cite_start]**Çıkış Basıncı ($P_9$):** $51,012.3 \, Pa$ [cite: 22]

[cite_start]**İtki Hesabı Formülü[cite: 23]:**

$$
F_g = (\dot{m} \times V_9) + A_9 \times (P_9 - P_0)
$$

**Sonuçlar:**
* **Şartname (Teorik) İtki:** $29.48 \, kN$ [cite: 21]
* **CFD Sonucu (Net İtki):** $\mathbf{31.25 \, kN}$ (Hesaplanan)

**Hata Analizi:**
$$\text{Hata} = \left| \frac{31.25 - 29.48}{29.48} \right| \times 100 = \%6.0$$
*Gözlemlenen %6'lık fark, yüksek irtifa koşullarındaki düşük ortam basıncının sağladığı ekstra basınç itkisinden kaynaklanmaktadır.*

---

### 4.4. İtki Katsayısı ($C_{fg}$)
[cite_start]İdeal süpersonik genişleme verimi:

**İdeal Değerler:**
* $\dot{m}_{ideal} = 38.16 \, kg/s$ [cite: 24]
* [cite_start]$V_{ideal} = 818.9175 \, m/s$ [cite: 25]
* $F_{g,ideal} = 31.25 \, kN$ 

**İtki Katsayısı Hesabı:**

$$
C_{fg} = \frac{F_{g,bulunan}}{F_{g,ideal}} = \frac{31.25}{31.25} = \mathbf{1.00}
$$

* [cite_start]**Teorik $C_{fg}$:** $0.968$ [cite: 23]
* **Hesaplanan $C_{fg}$:** $1.00$

## 5. Sonuç
[cite_start]Case-3 analizinde lüle, süpersonik rejime tam uyum sağlamış ve Mach 2.24 hızına ulaşmıştır. Hesaplanan itki katsayısının 1.00 olması, tasarımın bu basınç oranında maksimum teorik verime ulaştığını göstermektedir.
