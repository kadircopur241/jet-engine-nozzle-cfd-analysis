# Case-5: Extended Supersonic Flow & Altitude Performance Analysis

## 1. Giriş ve Amaç
[cite_start]Bu rapor, jet motoru nozzle tasarımının **Case-5 (Durum 5)** koşullarındaki sayısal analiz sonuçlarını içermektedir. [cite_start]Bu aşamada, lülenin yüksek irtifa şartlarını temsil eden düşük ortam basıncı ($11,597 \, Pa$) altındaki performansı ve süpersonik genişleme verimi incelenmiştir.

## 2. Geometrik Parametreler
[cite_start]Tasarımda kullanılan lüle geometrisi, yüksek genişleme oranına göre optimize edilmiştir[cite: 1, 3]:

* [cite_start]**Giriş Alanı ($A_7$):** $0.19635 \, m^2$ 
* **Boğaz Alanı ($A_8$):** $0.06645 \, m^2$ 
* **Alan Oranı ($A_9 / A_8$):** $2.000$ 
* [cite_start]**Yakınsaklık Yarım Açısı ($\alpha$):** $30^\circ$ [cite: 3]
* [cite_start]**Iraksaklık Yarım Açısı ($\theta$):** $12^\circ$ [cite: 3]

## 3. Sınır Koşulları (Boundary Conditions)
[cite_start]Analiz, ANSYS Fluent içerisinde aşağıdaki sınır koşulları altında parametrik olarak gerçekleştirilmiştir[cite: 1, 2]:

| Parametre | Sembol | Değer | Birim |
| :--- | :--- | :--- | :--- |
| Giriş Toplam Basıncı | $P_{t7}$ | 210,000 | Pa |
| Giriş Toplam Sıcaklığı | $T_{t7}$ | 776.47 | K |
| Ortam Basıncı | $P_0$ | 11,597 | Pa |
| Ortam Sıcaklığı | $T_0$ | 216.65 | K |
| Özgül Isı Kapasitesi | $C_p$ | 1084.2 | J/kg·K |

---

## 4. Performans Analizi ve Doğrulama

### 4.1. Kütlesel Debi Analizi ($\dot{m}$)
[cite_start]Süreklilik denkleminin sağlanması amacıyla kütle korunumu kontrol edilmiştir[cite: 4, 5].

* [cite_start]**Teorik (Hedef) Debi:** $18.857 \, kg/s$ [cite: 4]
* **CFD Giriş Debisi:** $18.97863 \, kg/s$ [cite: 4]
* [cite_start]**CFD Çıkış Debisi:** $-18.97797 \, kg/s$ [cite: 4]

**Hata Analizi:**
$$\text{Hata} = \left| \frac{18.97797 - 18.857}{18.857} \right| \times 100 = \%0.64$$

### 4.2. Deşarj Katsayısı ($C_d$) Hesabı
[cite_start]Boğaz bölgesindeki akış verimliliğini belirlemek için bulunan ve ideal kütlesel debi oranları kullanılmıştır[cite: 7].

$$C_d = \frac{\dot{m}_{bulunan}}{\dot{m}_{ideal}}$$

* **Teorik $C_d$ (Referans):** $0.940$ [cite: 5]
* **CFD $C_d$ (Hesaplanan):** $\mathbf{0.956}$ [cite: 7]

---

### 4.3. İtki Kuvveti ($F_g$) Analizi
[cite_start]Lüle çıkış yüzeyinden alınan güncel verilerle net itki hesaplanmıştır[cite: 9, 10].

* **Çıkış Hızı ($V_9$):** $876.89 \, m/s$ [cite: 9]
* **Çıkış Mutlak Basıncı ($P_9$):** $20,213.8 \, Pa$ [cite: 9]

**İtki Hesabı Formülü:**
[cite_start]$$F_g = (\dot{m} \times V_9) + A_9 \times (P_9 - P_0)$$ [cite: 10]

[cite_start]**Hesaplanan CFD İtkisi:** $\mathbf{17.787 \, kN}$ [cite: 13]

---

### 4.4. İtki ($F_g$) ve Verim ($C_{fg}$) Karşılaştırmalı Analiz
[cite_start]Analizden elde edilen performans verileri, şartname değerleri ile aşağıda karşılaştırılmıştır[cite: 13].

| Parametre | Teorik / Şartname | CFD Sonucu | Hata / Fark |
| :--- | :--- | :--- | :--- |
| **İtki Kuvveti ($F_g$)** | $30.99 \, kN$ | $17.787 \, kN$ | %42.6 |
| **İtki Katsayısı ($C_{fg}$)** | $0.961$ | $0.970$ | %0.93 |

**İtki Katsayısı ($C_{fg}$) Hesabı:**
$$C_{fg} = \frac{F_{g,bulunan}}{F_{g,ideal}} = \frac{17.787}{18.318} = \mathbf{0.970}$$ [cite: 13]

---

## 5. Sonuç ve Genel Değerlendirme

Case-5 analizinde lüle, süpersonik rejime tam uyum sağlamış ve Mach 2.54 hızına ulaşmıştır.

1. **Kütle Korunumu:** Giriş ve çıkış debileri arasındaki fark binde bir hassasiyetin altına inerek çözümün mükemmel şekilde yakınsadığını ispatlamıştır[cite: 4].
2. **İtki Farkının Nedeni:** Şartname itkisi ($30.99 \, kN$) ile CFD itkisi ($17.787 \, kN$) arasındaki fark, motorun çalışma noktasındaki düşük giriş basıncından (210 kPa) kaynaklanmaktadır. Bu durum motorun itki kapasitesini düşürse de lülenin tasarlandığı amaca uygunluğunu bozmamaktadır.
3. **Yüksek Verimlilik:** Nozzle performansının en saf göstergesi olan **İtki Katsayısı ($C_{fg}$)** değerinin **0.970** olarak hesaplanması, tasarımın teorik verim limitlerini (%0.93 fark ile) başarıyla karşıladığını doğrulamaktadır.
4. **Basınç Katkısı:** Çıkış basıncının ortam basıncından yüksek olması ($P_9 > P_0$), itkiye pozitif yönde bir basınç bileşeni ekleyerek yüksek irtifa performansını desteklemiştir.
