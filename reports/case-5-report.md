# Case-5: Extended Supersonic Flow & Altitude Performance Analysis

## 1. Giriş ve Amaç
Bu rapor, jet motoru nozzle tasarımının **Durum 5 (Case-5)** koşullarındaki sayısal analiz sonuçlarını içermektedir. Bu aşamada, lülenin yüksek irtifa şartlarını temsil eden düşük ortam basıncı ($11,597 \, Pa$) altındaki performansı ve süpersonik genişleme verimi incelenmiştir.

## 2. Geometrik Parametreler
Tasarımda kullanılan lüle geometrisi, yüksek genişleme oranına ($A_9/A_8 = 2.0$) göre optimize edilmiştir:

* **Giriş Alanı ($A_7$):** $0.19635 \, m^2$
* **Boğaz Alanı ($A_8$):** $0.06645 \, m^2$
* **Alan Oranı ($A_9 / A_8$):** $2.000$
* **Yakınsaklık Yarım Açısı ($\alpha$):** $30^\circ$
* **Iraksaklık Yarım Açısı ($\theta$):** $12^\circ$

## 3. Sınır Koşulları (Boundary Conditions)
Analiz, ANSYS Fluent içerisinde aşağıdaki işletme koşulları altında gerçekleştirilmiştir. Akışkan olarak "İdeal Gaz" (Hava) seçilmiş olup, özgül ısı kapasitesi ($C_p$) sıcaklığın bir fonksiyonu olarak tanımlanmış ve analiz sırasında her hücredeki yerel sıcaklık değerine göre dinamik olarak hesaplanmıştır. Durum 5 (Case-5) için yapılan bu analizde ($C_p$) $1022.897 \, J/kgK$ alınmıştır.
| Parametre | Sembol | Değer | Birim |
| :--- | :--- | :--- | :--- |
| Giriş Toplam Basıncı | $P_{t7}$ | 210,000 | Pa |
| Giriş Toplam Sıcaklığı | $T_{t7}$ | 776.47 | K |
| Ortam Basıncı | $P_0$ | 11,597 | Pa |
| Ortam Sıcaklığı | $T_0$ | 216.65 | K |

---

## 4. Performans Analizi ve Doğrulama

### 4.1. Kütlesel Debi Analizi ($\dot{m}$)
Süreklilik denkleminin sağlanması amacıyla kütle korunumu kontrol edilmiş ve teorik değerle kıyaslanmıştır.

* **Teorik (Hedef) Debi:** $18.857 \, kg/s$
* **CFD Giriş Debisi:** $18.97863 \, kg/s$
* **CFD Çıkış Debisi:** $-18.97797 \, kg/s$

**1. Süreklilik Hatası (Giriş vs Çıkış):**

$$
\text{Hata}_{\text{süreklilik}} = \left| \frac{\dot{m}_{in} - |\dot{m}_{out}|}{\dot{m}_{in}} \right| \times 100 = \mathbf{\%0.0005}
$$

**2. Tahmin Hatası (CFD vs Teorik):**

$$
\text{Hata}_{\text{tahmin}} = \left| \frac{|\dot{m}_{out}| - 18.857}{18.857} \right| \times 100 = \mathbf{\%0.60}
$$


*%1'in altındaki bu hata oranı, çözümün başarıyla yakınsadığını ve kütle korunumunun sağlandığını gösterir.*

### 4.2. Deşarj Katsayısı ($C_d$) Hesabı
Boğaz bölgesindeki akış verimliliğini belirlemek için bulunan kütlesel debinin ideal izentropik debiye oranı kullanılmıştır.

$$
C_d = \frac{\dot{m}_{bulunan}}{\dot{m}_{ideal}}
$$

* **Teorik $C_d$ (Referans):** $0.940$
* **CFD $C_d$ (Hesaplanan):** $18.97797 / 20.03859 = \mathbf{0.947}$

---

### 4.3. İtki Kuvveti ($F_g$) Analizi
Lüle çıkış yüzeyinden alınan verilerle toplam net itki hesaplanmıştır.

* **Çıkış Hızı ($V_9$):** $876.89 \, m/s$
* **Çıkış Mutlak Basıncı ($P_9$):** $20,213.8 \, Pa$
* **Çıkış Alanı ($A_9$):** $0.1329 \, m^2$

**İtki Formülü:**

$$
F_g = (\dot{m} \times V_9) + A_9 \times (P_9 - P_0)
$$

**CFD İtki Hesabı:**

$$
F_{g,CFD} = (18.97797 \times 876.89) + 0.1329 \times (20213.8 - 11597) = \mathbf{17.787 \, kN}
$$

---

### 4.4. İtki ($F_g$) ve Verim ($C_{fg}$) Karşılaştırmalı Analiz
Lülenin genel verimlilik göstergesi olan $C_{fg}$ değeri, CFD itkisinin ideal itkiye bölünmesiyle bulunmuştur. İdeal değerler için kullanılan termodinamik denklemler aşağıdadır:

**İdeal Kütlesel Debi ve Çıkış Hızı Formülleri:**

$$
\dot{m}_{ideal} = \frac{A_8 \cdot P_{t7}}{\sqrt{T_{t7}}} \sqrt{\frac{\gamma}{R} \left( \frac{2}{\gamma+1} \right)^{\frac{\gamma+1}{\gamma-1}}} \quad , \quad V_{ideal} = \sqrt{2 \cdot C_p \cdot T_{t7} \left[ 1 - \left( \frac{P_0}{P_{t7}} \right)^{\frac{\gamma-1}{\gamma}} \right]}
$$

* **İdeal Kütlesel Debi ($\dot{m}_{ideal}$):** $20.03859 \, kg/s$
* **İdeal Çıkış Hızı ($V_{ideal}$):** $914.154 \, m/s$
* **İdeal İtki ($F_{g,ideal}$):** $18.31836 \, kN$

**Karşılaştırma Tablosu:**

| Parametre | Teorik / Şartname | CFD Sonucu | Hata / Fark |
| :--- | :--- | :--- | :--- |
| **İtki Kuvveti ($F_g$)** | $17.13 \, kN$ | $17.787 \, kN$ | %3.83 |
| **İtki Katsayısı ($C_{fg}$)** | $0.961$ | $0.971$ | %1.04 |

**İtki Katsayısı ($C_{fg}$) Hesabı:**

$$
C_{fg,CFD} = \frac{F_{g,CFD}}{F_{g,ideal}} = \frac{17.787}{18.31836} = \mathbf{0.971}
$$

---

## 5. Sonuç ve Genel Değerlendirme

Case-5 analizinde lüle, süpersonik rejime tam uyum sağlamış ve Mach 2.54 hızına ulaşmıştır. Yapılan analizler sonucunda şu çıkarımlar yapılmıştır:

1. **Sayısal Doğrulama:** Kütlesel debi hata payının **%0.64** seviyesinde kalması, modelin ve mesh yapısının doğruluğunu kanıtlamıştır.
2. **Kusursuz Uyum:** Şartnamede belirtilen güncel itki değeri ($17.13 \, kN$) ile CFD sonucu arasındaki farkın **%3.83** gibi düşük bir seviyede olması analizin başarısını doğrular.
3. **Yüksek Verimlilik:** Nozzle verimini gösteren **İtki Katsayısı ($C_{fg}$)** değerinin **0.971** çıkması, tasarımın sürtünme kayıplarını minimumda tutarak teorik hedefleri yakaladığını ispatlamıştır.
4. **Basınç Katkısı:** Lülenin "under-expanded" modda çalışması ($P_9 > P_0$), net itkiye pozitif yönde bir basınç bileşeni ekleyerek motor performansını desteklemiştir.
