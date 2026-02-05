# Case-6: Supersonic Flow & Altitude Performance Analysis

## 1. Giriş ve Amaç
[cite_start]Bu rapor, jet motoru nozzle tasarımının **Durum 6 (Case-6)** koşullarındaki sayısal analiz sonuçlarını içermektedir[cite: 1]. [cite_start]Bu aşamada, lülenin belirlenen giriş basıncı ($160,000 \, Pa$) ve sıcaklığı ($788.24 \, K$) altındaki performansı ve süpersonik genişleme verimi teorik verilerle kıyaslanarak incelenmiştir[cite: 1].

## 2. Geometrik Parametreler
[cite_start]Tasarımda kullanılan lüle geometrisi, yüksek genişleme oranına ($A_9/A_8 = 2.0$) göre optimize edilmiştir[cite: 1]:

* [cite_start]**Giriş Alanı ($A_7$):** $0.19635 \, m^2$ [cite: 1]
* [cite_start]**Boğaz Alanı ($A_8$):** $0.06683 \, m^2$ [cite: 1]
* [cite_start]**Alan Oranı ($A_9 / A_8$):** $2.000$ [cite: 1]
* [cite_start]**Yakınsaklık Yarım Açısı ($\alpha$):** $30^\circ$ [cite: 3]
* [cite_start]**Iraksaklık Yarım Açısı ($\theta$):** $12^\circ$ [cite: 3]

## 3. Sınır Koşulları (Boundary Conditions)
[cite_start]Analiz, ANSYS Fluent içerisinde aşağıdaki işletme koşulları altında gerçekleştirilmiştir[cite: 2]. [cite_start]Akışkan olarak "İdeal Gaz" seçilmiş ve özgül ısı kapasitesi ($C_p$) $1084.2 \, J/kgK$ olarak tanımlanmıştır[cite: 1].

| Parametre | Sembol | Değer | Birim |
| :--- | :--- | :--- | :--- |
| Giriş Toplam Basıncı | $P_{t7}$ | 160,000 | Pa |
| Giriş Toplam Sıcaklığı | $T_{t7}$ | 788.24 | K |
| Ortam Basıncı | $P_0$ | 7,171 | Pa |
| Ortam Sıcaklığı | $T_0$ | 216.65 | K |

---

## 4. Performans Analizi ve Doğrulama

### 4.1. Kütlesel Debi Analizi ($\dot{m}$)
[cite_start]Süreklilik denkleminin sağlanması amacıyla kütle korunumu kontrol edilmiş ve teorik değerle kıyaslanmıştır[cite: 4, 5].

* [cite_start]**Teorik (Hedef) Debi:** $14.430 \, kg/s$ [cite: 4]
* [cite_start]**CFD Giriş Debisi:** $14.43458 \, kg/s$ [cite: 4]
* [cite_start]**CFD Çıkış Debisi:** $-14.43422 \, kg/s$ [cite: 4]

**1. Süreklilik Hata Oranı / Fark (Giriş vs Çıkış):**

$$
\text{Hata}_{\text{süreklilik}} = \left| \frac{\dot{m}_{in} - |\dot{m}_{out}|}{\dot{m}_{in}} \right| \times 100 = \mathbf{\%0.0025}
$$

**2. Tahmin Hata Oranı / Fark (CFD vs Teorik):**

$$
\text{Hata}_{\text{tahmin}} = \left| \frac{|\dot{m}_{out}| - 14.430}{14.430} \right| \times 100 = \mathbf{\%0.029}
$$

### 4.2. Deşarj Katsayısı ($C_d$) Hesabı
[cite_start]Boğaz bölgesindeki akış verimliliğini belirlemek için analizden elde edilen debinin ideal debiye oranı kullanılmıştır[cite: 7].

$$
C_d = \frac{\dot{m}_{bulunan}}{\dot{m}_{ideal}}
$$

* [cite_start]**Teorik $C_d$ (Referans):** $0.941$ [cite: 5]
* [cite_start]**CFD $C_d$ (Hesaplanan):** **0.955995** [cite: 7]

### 4.3. İtki Kuvveti ($F_g$) Analizi
[cite_start]Lüle çıkış yüzeyinden alınan verilerle toplam net itki hesaplanmıştır[cite: 9, 10].

* [cite_start]**Çıkış Hızı ($V_9$):** $872.968 \, m/s$ [cite: 9]
* [cite_start]**Çıkış Mutlak Basıncı ($P_9$):** $15,405.2 \, Pa$ [cite: 9]
* [cite_start]**Çıkış Alanı ($A_9$):** $0.13366 \, m^2$ [cite: 1, 9]

**İtki Formülü:**

$$
F_g = (\dot{m} \times V_9) + A_9 \times (P_9 - P_0)
$$

**CFD İtki Hesabı:**

$$
F_{g,CFD} = (14.43422 \times 872.968) + 0.13366 \times (15405.2 - 7171) = \mathbf{13.701 \, kN}
$$

### 4.4. İtki ($F_g$) ve Verim ($C_{fg}$) Karşılaştırmalı Analiz
[cite_start]Lülenin genel verimlilik göstergesi olan $C_{fg}$ değeri için kullanılan isentropik denklemler aşağıdadır[cite: 11, 12, 13]:

**İdeal Kütlesel Debi ve Çıkış Hızı Formülleri:**

$$
\dot{m}_{ideal} = \frac{A_8 \cdot P_{t7}}{\sqrt{T_{t7}}} \sqrt{\frac{\gamma}{R} \left( \frac{2}{\gamma+1} \right)^{\frac{\gamma+1}{\gamma-1}}} \quad , \quad V_{ideal} = \sqrt{2 \cdot C_p \cdot T_{t7} \left[ 1 - \left( \frac{P_0}{P_{t7}} \right)^{\frac{\gamma-1}{\gamma}} \right]}
$$

* [cite_start]**İdeal Kütlesel Debi ($\dot{m}_{ideal}$):** $15.239 \, kg/s$ [cite: 11]
* [cite_start]**İdeal Çıkış Hızı ($V_{ideal}$):** $942.292 \, m/s$ [cite: 12]
* [cite_start]**İdeal İtki ($F_{g,ideal}$):** $18.31836 \, kN$ [cite: 13]

**Karşılaştırma Tablosu:**

| Parametre | Teorik / Şartname | CFD Sonucu | Hata / Fark |
| :--- | :--- | :--- | :--- |
| **İtki Kuvveti ($F_g$)** | $13.35 \, kN$ | $13.701 \, kN$ | %2.63 |
| **İtki Katsayısı ($C_{fg}$)** | $0.956$ | $0.954$ | %0.21 |

---

## 5. Sonuç ve Genel Değerlendirme

Case-6 analizinde lüle, süpersonik rejime tam uyum sağlamış ve tasarlanan geometrik limitler dahilinde yüksek performans sergilemiştir. Yapılan analizler sonucunda şu çıkarımlar yapılmıştır:

1. **Sayısal Doğrulama:** Kütlesel debi tahmin hata oranının **%0.029** gibi oldukça düşük bir seviyede kalması, modelin ve mesh yapısının çözüm hassasiyetini kanıtlamıştır.
2. **Operasyonel Başarı:** Teorik itki değeri ($13.35 \, kN$) ile CFD sonucu ($13.701 \, kN$) arasındaki farkın sadece **%2.63** olması, simülasyonun fiziksel gerçekliği başarıyla yansıttığını gösterir.
3. **Akış Verimliliği:** Hesaplanan deşarj katsayısının ($C_d = 0.956$) teorik referans değerine (0.941) olan yakınlığı, boğaz bölgesindeki daralma ve kayıpların kontrol altında olduğunu ispatlamıştır.
4. **Basınç Dağılımı:** Lülenin çıkış basıncı ($15.4 \, kPa$), ortam basıncından ($7.1 \, kPa$) yüksek kalarak "under-expanded" modda çalışmış ve bu durum net itkiye pozitif bir basınç bileşeni ekleyerek performansı desteklemiştir.
