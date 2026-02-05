# Case-6: Supersonic Flow & Altitude Performance Analysis

## 1. Giriş ve Amaç
Bu rapor, jet motoru nozzle tasarımının **Durum 6 (Case-6)** koşullarındaki sayısal analiz sonuçlarını içermektedir. Bu aşamada, lülenin belirlenen giriş basıncı ($160,000 \, Pa$) ve sıcaklığı ($788.24 \, K$) altındaki performansı ve süpersonik genişleme verimi teorik verilerle kıyaslanarak incelenmiştir.

## 2. Geometrik Parametreler
Tasarımda kullanılan lüle geometrisi, yüksek genişleme oranına ($A_9/A_8 = 2.0$) göre optimize edilmiştir:

* **Giriş Alanı ($A_7$):** $0.19635 \, m^2$
* **Boğaz Alanı ($A_8$):** $0.06683 \, m^2$
* **Alan Oranı ($A_9 / A_8$):** $2.000$
* **Yakınsaklık Yarım Açısı ($\alpha$):** $30^\circ$
* **Iraksaklık Yarım Açısı ($\theta$):** $12^\circ$

## 3. Sınır Koşulları (Boundary Conditions)
Analiz, ANSYS Fluent içerisinde aşağıdaki işletme koşulları altında gerçekleştirilmiştir. Akışkan olarak "İdeal Gaz" seçilmiş ve özgül ısı kapasitesi ($C_p$) $1084.2 \, J/kgK$ olarak tanımlanmıştır.

| Parametre | Sembol | Değer | Birim |
| :--- | :--- | :--- | :--- |
| Giriş Toplam Basıncı | $P_{t7}$ | 160,000 | Pa |
| Giriş Toplam Sıcaklığı | $T_{t7}$ | 788.24 | K |
| Ortam Basıncı | $P_0$ | 7,171 | Pa |
| Ortam Sıcaklığı | $T_0$ | 216.65 | K |

---

## 4. Performans Analizi ve Doğrulama

### 4.1. Kütlesel Debi Analizi ($\dot{m}$)
Süreklilik denkleminin sağlanması amacıyla kütle korunumu kontrol edilmiş ve teorik değerle kıyaslanmıştır.

* **Teorik (Hedef) Debi:** $14.430 \, kg/s$
* **CFD Giriş Debisi:** $14.43458 \, kg/s$
* **CFD Çıkış Debisi:** $-14.43422 \, kg/s$

**1. Süreklilik Hata Oranı / Fark (Giriş vs Çıkış):**

$$
\text{Hata}_{\text{süreklilik}} = \left| \frac{\dot{m}_{in} - |\dot{m}_{out}|}{\dot{m}_{in}} \right| \times 100 = \mathbf{\%0.0025}
$$

**2. Tahmin Hata Oranı / Fark (CFD vs Teorik):**

$$
\text{Hata}_{\text{tahmin}} = \left| \frac{|\dot{m}_{out}| - 14.430}{14.430} \right| \times 100 = \mathbf{\%0.029}
$$

*%1'in altındaki bu hata oranı, çözümün başarıyla yakınsadığını ve kütle korunumunun sağlandığını gösterir.*

### 4.2. Deşarj Katsayısı ($C_d$) Hesabı
Boğaz bölgesindeki akış verimliliğini belirlemek için analizden elde edilen debinin ideal debiye oranı kullanılmıştır.

$$
C_d = \frac{\dot{m}_{bulunan}}{\dot{m}_{ideal}}
$$

* **Teorik $C_d$ (Referans):** $0.941$
* **CFD $C_d$ (Hesaplanan):** **0.9471**

### 4.3. İtki Kuvveti ($F_g$) Analizi
Lüle çıkış yüzeyinden alınan verilerle toplam net itki hesaplanmıştır.

* **Çıkış Hızı ($V_9$):** $872.968 \, m/s$
* **Çıkış Mutlak Basıncı ($P_9$):** $15,405.2 \, Pa$
* **Çıkış Alanı ($A_9$):** $0.13366 \, m^2$

**İtki Formülü:**

$$
F_g = (\dot{m} \times V_9) + A_9 \times (P_9 - P_0)
$$

**CFD İtki Hesabı:**

$$
F_{g,CFD} = (14.43422 \times 872.968) + 0.13366 \times (15405.2 - 7171) = \mathbf{13.701 \, kN}
$$

### 4.4. İtki ($F_g$) ve Verim ($C_{fg}$) Karşılaştırmalı Analiz
Lülenin genel verimlilik göstergesi olan $C_{fg}$ değeri için kullanılan isentropik denklemler aşağıdadır:

**İdeal Kütlesel Debi ve Çıkış Hızı Formülleri:**

$$
\dot{m}_{ideal} = \frac{A_8 \cdot P_{t7}}{\sqrt{T_{t7}}} \sqrt{\frac{\gamma}{R} \left( \frac{2}{\gamma+1} \right)^{\frac{\gamma+1}{\gamma-1}}} \quad , \quad V_{ideal} = \sqrt{2 \cdot C_p \cdot T_{t7} \left[ 1 - \left( \frac{P_0}{P_{t7}} \right)^{\frac{\gamma-1}{\gamma}} \right]}
$$

* **İdeal Kütlesel Debi ($\dot{m}_{ideal}$):** $15.239 \, kg/s$
* **İdeal Çıkış Hızı ($V_{ideal}$):** $942.292 \, m/s$
* **İdeal İtki ($F_{g,ideal}$):** **$14.360 \, kN$**

**Karşılaştırma Tablosu:**

| Parametre | Teorik / Şartname | CFD Sonucu | Hata / Fark |
| :--- | :--- | :--- | :--- |
| **İtki Kuvveti ($F_g$)** | $13.35 \, kN$ | $13.701 \, kN$ | %2.63 |
| **İtki Katsayısı ($C_{fg}$)** | $0.956$ | **0.954** | %0.21 |

---

## 5. Sonuç ve Genel Değerlendirme

Case-6 analizinde lüle, süpersonik rejime tam uyum sağlamış ve tasarlanan geometrik limitler dahilinde yüksek performans sergilemiştir. Yapılan analizler sonucunda şu çıkarımlar yapılmıştır:

1. **Sayısal Doğrulama:** Kütlesel debi tahmin hata oranının **%0.029** gibi oldukça düşük bir seviyede kalması, modelin ve mesh yapısının çözüm hassasiyetini kanıtlamıştır.
2. **Operasyonel Başarı:** Teorik itki değeri ($13.35 \, kN$) ile CFD sonucu ($13.701 \, kN$) arasındaki farkın sadece **%2.63** olması, simülasyonun fiziksel gerçekliği başarıyla yansıttığını gösterir.
3. **Akış Verimliliği:** Hesaplanan deşarj katsayısının ($C_d = 0.9471$) teorik referans değerine (0.941) olan yüksek yakınlığı, boğaz bölgesindeki daralma ve kayıpların son derece düşük olduğunu ispatlamıştır.
4. **Basınç Dağılımı:** Lülenin çıkış basıncı ($15.4 \, kPa$), ortam basıncından ($7.1 \, kPa$) yüksek kalarak "under-expanded" modda çalışmış ve bu durum net itkiye pozitif bir basınç bileşeni ekleyerek performansı desteklemiştir.
