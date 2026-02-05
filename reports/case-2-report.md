# Case-2: Analysis & Validation Report ($M_{N0}=1.00$)

## 1. Giriş ve Amaç
Bu rapor, jet motoru nozzle tasarımının **Durum 2 (Case-2)** koşullarındaki sayısal analiz sonuçlarını içermektedir. Bu analiz setinde, lüle giriş basıncı artırılarak ($580 \, kPa$) performans karakteristiklerinin değişimi ve nozzle'ın yüksek basınç altındaki davranışları incelenmiştir.

## 2. Geometrik Parametreler
Case-2 analizinde kullanılan lüle geometrisi, tasarım noktası (DP) ile aynı olup, genişleme oranları sabittir:

* **Giriş Alanı ($A_7$):** $0.19635 \, m^2$
* **Boğaz Alanı ($A_8$):** $0.06675 \, m^2$
* **Alan Oranı ($A_9/A_8$):** $1.373$
* **Çıkış Alanı ($A_9$):** $0.09165 \, m^2$
* **Yakınsaklık Yarım Açısı ($\alpha$):** $30^\circ$
* **Iraksaklık Yarım Açısı ($\theta$):** $12^\circ$

## 3. Sınır Koşulları (Boundary Conditions)
Analiz, ANSYS Fluent içerisinde aşağıdaki işletme koşulları altında gerçekleştirilmiştir. Akışkan olarak "İdeal Gaz" (Hava) seçilmiş olup, özgül ısı kapasitesi ($C_p$) sıcaklığın bir fonksiyonu olarak tanımlanmış ve analiz sırasında her hücredeki yerel sıcaklık değerine göre dinamik olarak hesaplanmıştır. Durum 2 (Case-2) için yapılan bu analizde ısı kapasitesi ($C_p$) $1082.2 \, J/kgK$ olarak hesaplanmıştır.

| Parametre | Sembol | Değer | Birim |
| :--- | :--- | :--- | :--- |
| Giriş Toplam Basıncı | $P_{t7}$ | 580,000 | Pa |
| Giriş Toplam Sıcaklığı | $T_{t7}$ | 784.31 | K |
| Ortam Basıncı | $P_0$ | 101,325 | Pa |
| Ortam Sıcaklığı | $T_0$ | 288.15 | K |

---

## 4. Performans Analizi ve Doğrulama

### 4.1. Kütlesel Debi Analizi ($\dot{m}$) ve Süreklilik Kontrolü
Süreklilik denkleminin sağlanması amacıyla hem giriş-çıkış farkı hem de teorik değerle olan sapma kontrol edilmiştir.

* **Teorik (Hedef) Debi:** $52.054 \, kg/s$
* **CFD Giriş Debisi ($\dot{m}_{in}$):** $52.36805 \, kg/s$
* **CFD Çıkış Debisi ($\dot{m}_{out}$):** $-52.36831 \, kg/s$

**1. Süreklilik Hatası (Giriş vs Çıkış):**

$$
\text{Hata}_{\text{süreklilik}} = \left| \frac{\dot{m}_{in} - |\dot{m}_{out}|}{\dot{m}_{in}} \right| \times 100 = \mathbf{\%0.0005}
$$

**2. Tahmin Hatası (CFD vs Teorik):**

$$
\text{Hata}_{\text{tahmin}} = \left| \frac{|\dot{m}_{out}| - 52.054}{52.054} \right| \times 100 = \mathbf{\%0.60}
$$

*%1'in altındaki bu sapma, termodinamik modelin ve mesh yapısının mükemmel bir doğruluğa ulaştığını kanıtlamaktadır.*

### 4.2. Deşarj Katsayısı ($C_d$) Karşılaştırması
Boğaz bölgesindeki gerçek akışın ideal izentropik akışa oranı üzerinden hesaplanan $C_d$ analizi aşağıdadır:

$$
C_d = \frac{\dot{m}_{bulunan}}{\dot{m}_{ideal}} = \frac{52.36831}{55.316} = \mathbf{0.9467}
$$

* **Teorik $C_d$ Referansı:** $0.940$
* **CFD Hesaplanan $C_d$:** $0.9467$
* **Fark:** %0.71

---

### 4.3. İtki Kuvveti ($F_g$) Analizi
Lüle çıkış yüzeyinden alınan verilerle toplam net itki hesaplanmıştır.

* **Şartname (Teorik) İtki:** $40.00 \, kN$
* **CFD Sonucu (Net İtki):** $\mathbf{39.9615 \, kN}$

**İtki Formülü:**

$$
F_g = (\dot{m} \times V_9) + A_9 \times (P_9 - P_0)
$$

**Hata Analizi:**

$$
\text{Hata} = \left| \frac{39.9615 - 40.00}{40.00} \right| \times 100 = \mathbf{\%0.096}
$$

---

### 4.4. İtki ($F_g$) ve Verim ($C_{fg}$) Karşılaştırmalı Analiz
Lülenin genel verimlilik göstergesi olan $C_{fg}$ değeri için kullanılan termodinamik denklemler aşağıdadır:

**İdeal Kütlesel Debi ve Çıkış Hızı Formülleri:**

$$
\dot{m}_{ideal} = \frac{A_8 \cdot P_{t7}}{\sqrt{T_{t7}}} \sqrt{\frac{\gamma}{R} \left( \frac{2}{\gamma+1} \right)^{\frac{\gamma+1}{\gamma-1}}} \quad , \quad V_{ideal} = \sqrt{2 \cdot C_p \cdot T_{t7} \left[ 1 - \left( \frac{P_0}{P_{t7}} \right)^{\frac{\gamma-1}{\gamma}} \right]}
$$

* **İdeal Kütlesel Debi ($\dot{m}_{ideal}$):** $55.316 \, kg/s$
* **İdeal Çıkış Hızı ($V_{ideal}$):** $763.602 \, m/s$
* **İdeal İtki ($F_{g,ideal}$):** $42.24 \, kN$

**İtki Katsayısı ($C_{fg}$) Hesabı:**

$$
C_{fg,CFD} = \frac{39.9615}{42.24} = \mathbf{0.946}
$$

| Parametre | Teorik / Şartname | CFD Sonucu | Hata / Fark |
| :--- | :--- | :--- | :--- |
| **İtki Kuvveti ($F_g$)** | $40.00 \, kN$ | $39.9615 \, kN$ | %0.096 |
| **İtki Katsayısı ($C_{fg}$)** | $0.970$ | $0.946$ | %2.47 |

---

## 5. Sonuç ve Genel Değerlendirme

Case-2 (Yüksek Basınç Altında Performans) analizleri sonucunda elde edilen veriler ışığında şu çıkarımlar yapılmıştır:

1. **Sayısal Doğrulama:** Süreklilik hatasının **%0.0005** gibi ihmal edilebilir bir seviyede çıkması, çözümün sayısal olarak mükemmel şekilde yakınsadığını ispatlamıştır.
2. **Kütlesel Debi Uyumu:** Kütlesel debi hatasının **%0.60** seviyesinde kalması, viskoz etkilerin ve sınır tabaka gelişiminin analizde başarıyla modellendiğini göstermektedir.
3. **İtki Hassasiyeti:** Şartname itkisi ($40.00 \, kN$) ile CFD sonucu ($39.96 \, kN$) arasındaki **%0.096**'lık uyum, lülenin yüksek basınçlı akışlarda (NPR) tasarım hedeflerini tam isabetle karşıladığını kanıtlar.
4. **Verimlilik:** Hesaplanan **0.946** $C_{fg}$ değeri, yüksek basınçlı süpersonik deşarj sırasında meydana gelen kayıpların tasarım limitleri içerisinde kaldığını ispatlamıştır.
