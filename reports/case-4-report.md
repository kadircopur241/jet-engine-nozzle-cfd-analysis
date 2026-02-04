# Case-4: High Supersonic Expansion & Performance Validation

## 1. Giriş ve Amaç
Bu rapor, lüle tasarımının **Case-4 (Durum 4)** koşullarındaki sayısal analiz sonuçlarını içermektedir. Bu aşamada, yüksek basınç farkı altında lülenin süpersonik deşarj kapasitesi ve elde edilen itki kuvvetinin teorik değerlerle doğrulanması amaçlanmıştır.

## 2. Geometrik Parametreler
Tasarımda kullanılan lüle geometrisi, yüksek genişleme oranına göre optimize edilmiştir:

* **Giriş Alanı ($A_7$):** $0.19635 \, m^2$
* **Boğaz Alanı ($A_8$):** $0.06709 \, m^2$
* **Alan Oranı ($A_9 / A_8$):** $2.000$
* **Çıkış Alanı ($A_9$):** $0.13418 \, m^2$ (Hesaplanan)
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
Lüle çıkış yüzeyinden alınan verilerle net itki hesaplanmıştır.

* **Çıkış Hızı ($V_9$):** $876.89 \, m/s$
* **Çıkış Basıncı ($P_9$):** $165,286.3 \, Pa$

**İtki Hesabı Formülü:**

$$
F_g = (\dot{m} \times V_9) + A_9 \times (P_9 - P_0)
$$

**Sonuçlar:**
* **Şartname (Teorik) İtki:** $30.99 \, kN$
* **CFD Sonucu (Net İtki):** $\mathbf{31.52 \, kN}$

---

### 4.4. İtki ($F_g$) ve Verim ($C_{fg}$) Karşılaştırmalı Analiz
Analizden elde edilen performans verileri ile teorik referanslar arasındaki ilişki aşağıda özetlenmiştir.

| Parametre | Teorik / Şartname | CFD Sonucu | Hata / Fark |
| :--- | :--- | :--- | :--- |
| **İtki Kuvveti ($F_g$)** | $30.99 \, kN$ | $31.52 \, kN$ | %1.71 |
| **İtki Katsayısı ($C_{fg}$)** | $0.966$ | $0.957$ | %0.93 |

**İtki Katsayısı ($C_{fg}$) Hesabı:**

$$
C_{fg} = \frac{F_{g,bulunan}}{F_{g,ideal}} = \frac{31.52}{32.9398} = \mathbf{0.957}
$$

**Değerlendirme:**
* **İtki:** CFD sonucu şartname değerinden %1.71 daha yüksek çıkmıştır. Bu durum, çıkış basıncının ortam basıncından yüksek olması ($P_9 > P_0$) nedeniyle oluşan ek basınç itkisinden kaynaklanır.
* **Verim:** Hesaplanan $0.957$ değeri, teorik $0.966$ referansına oldukça yakındır. Aradaki %0.93'lük fark, süpersonik akıştaki sürtünme ve sınır tabaka kayıplarını temsil eder.

## 5. Sonuç ve Genel Değerlendirme
Case-4 analizleri sonucunda lüle, yüksek süpersonik hızlarda (**Mach 2.55**) stabil bir çalışma sergilemiştir.

1. **Süreklilik:** Giriş-çıkış kütlesel debi farkı binde bir mertebesinde kalarak sayısal çözümün başarıyla yakınsadığını göstermiştir.
2. **Hassasiyet:** Teorik debi ile analiz sonucu arasındaki hata **%0.587** gibi oldukça düşük bir seviyededir.
3. **Doğrulama:** Hesaplanan itki ve verimlilik katsayıları, tasarlanan geometrinin yüksek irtifa basınç oranlarında teorik tasarım kriterlerini tam tutarlılıkla karşıladığını ispatlamaktadır.
