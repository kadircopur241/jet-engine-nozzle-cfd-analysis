# Case-2: Analysis & Validation Report ($M_{N0}=1.00$)

## 1. Giriş ve Amaç
Bu rapor, jet motoru nozzle tasarımının **Case-2 (Durum 2)** koşullarındaki sayısal analiz sonuçlarını içermektedir. Bu analiz setinde, lüle giriş basıncı artırılarak (580 kPa) performans karakteristiklerinin değişimi ve nozzle'ın yüksek basınç altındaki davranışları incelenmiştir.

## 2. Geometrik Parametreler
Case-2 analizinde kullanılan lüle geometrisi, tasarım noktası (DP) ile aynı olup, genişleme oranları sabittir:

* **Giriş Alanı ($A_7$):** $0.19635 \, m^2$
* **Boğaz Alanı ($A_8$):** $0.06675 \, m^2$
* **Alan Oranı ($A_9/A_8$):** $1.373$
* **Çıkış Alanı ($A_9$):** $0.09165 \, m^2$ (Hesaplanan)
* **Yakınsaklık Yarım Açısı ($\alpha$):** $30^\circ$
* **Iraksaklık Yarım Açısı ($\theta$):** $12^\circ$

## 3. Sınır Koşulları (Boundary Conditions)
Analiz, ANSYS Fluent içerisinde aşağıdaki işletme koşulları altında gerçekleştirilmiştir.

| Parametre | Sembol | Değer | Birim |
| :--- | :--- | :--- | :--- |
| Giriş Toplam Basıncı | $P_{t7}$ | 580,000 | Pa |
| Giriş Toplam Sıcaklığı | $T_{t7}$ | 784.31 | K |
| Ortam Basıncı | $P_0$ | 101,325 | Pa |
| Ortam Sıcaklığı | $T_0$ | 288.15 | K |

---

## 4. Performans Analizi ve Doğrulama

### 4.1. Kütlesel Debi Analizi ($\dot{m}$)
Süreklilik denkleminin sağlanması kontrol edilmiştir. Giriş basıncının artmasıyla birlikte kütlesel debide beklenen artış gözlemlenmiştir.

* **Teorik (Hedef) Debi:** $52.054 \, kg/s$
* **CFD Giriş Debisi:** $52.8626 \, kg/s$
* **CFD Çıkış Debisi:** $-52.8616 \, kg/s$ (Net akış)

**Hata Analizi:**

$$
\text{Hata} = \left| \frac{52.8616 - 52.054}{52.054} \right| \times 100 = \%1.55
$$

*%1.55'lik sapma, sıkıştırılabilir akış analizleri için oldukça kabul edilebilir bir aralıktadır.*

### 4.2. Deşarj Katsayısı ($C_d$) Hesabı
Efektif akış alanının doğrulanması amacıyla Deşarj Katsayısı hesaplanmıştır.

**Kullanılan Formül:**

$$
C_d = \frac{\dot{m}_{bulunan}}{\dot{m}_{ideal}}
$$

Termodinamik denklemlerle hesaplanan **İdeal (Isentropic) Kütlesel Debi ($\dot{m}_{ideal}$)** değeri **$55.316 \, kg/s$** olarak referans alınmıştır (Bkz. Bölüm 4.4).

* **Teorik $C_d$ (Referans):** $0.940$
* **CFD $C_d$ (Hesaplanan):** $0.9467$

**Karşılaştırma:**
Referans değer ile analiz sonucu arasındaki fark binde 7 mertebesindedir. Mesh yapısının sınır tabaka etkilerini ($boundary layer$) başarıyla modellediği görülmektedir.

---

### 4.3. İtki Kuvveti ($F_g$) Analizi
Analiz sonucunda lüle çıkış düzleminden (Station 9) alınan ortalama veriler şöyledir:
* **Çıkış Hızı ($V_9$):** $749.714 \, m/s$
* **Çıkış Basıncı ($P_9$):** $144,265 \, Pa$
* **Çıkış Alanı ($A_9$):** $0.09165 \, m^2$

**İtki Hesabı Formülü:**

$$
F_g = (\dot{m} \times V_9) + A_9 \times (P_9 - P_0)
$$

**Hesaplama:**
$$
F_{g,CFD} = (52.8616 \times 749.714) + 0.09165 \times (144265 - 101325)
$$

$$
F_{g,CFD} \approx 39,631 + (0.09165 \times 42,940)
$$

$$
F_{g,CFD} \approx 39,631 + 3,935 = 43,566 \, N \approx \mathbf{43.57 \, kN}
$$

**Doğrulama:**
* **Şartname (Teorik) İtki:** $40.00 \, kN$
* **CFD Sonucu:** $43.57 \, kN$
* **Yorum:** Çıkış basıncının ($P_9$), ortam basıncından ($P_0$) yüksek olması (underexpanded condition), "Pressure Thrust" teriminin itkiye ekstra katkı sağlamasına neden olmuş ve toplam itki teorik hedefin üzerine çıkmıştır.

---

### 4.4. İtki Katsayısı ($C_{fg}$)
İdeal koşullardaki performans ile gerçek performansın kıyaslanmasıdır.

**İdeal Değerler:**
* $\dot{m}_{ideal} = 55.316 \, kg/s$
* $V_{ideal} = 763.602 \, m/s$

$$
F_{g,ideal} = \dot{m}_{ideal} \times V_{ideal} = 55.316 \times 763.602 \approx \mathbf{42.24 \, kN}
$$

**İtki Katsayısı Hesabı:**

$$
C_{fg} = \frac{F_{g,bulunan}}{F_{g,ideal}} = \frac{43.57}{42.24} = 1.03
$$

* **Teorik $C_{fg}$:** $0.970$
* **Hesaplanan $C_{fg}$:** $1.03$

**Sonuç ve Yorum:**
Hesaplanan $C_{fg}$ değerinin 1'in üzerinde çıkması, nozzle'ın bu basınç oranında tam genişleme sağlayamadığını (underexpanded) ve çıkış basınç farkından doğan ekstra itkinin ($Pressure Thrust$), sürtünme kayıplarını ($Velocity Loss$) domine ettiğini göstermektedir.

## 5. Sonuç
Case-2 koşullarında yapılan analizlerde:
1. Kütlesel debi hatası **%1.55**,
2. Deşarj katsayısı ($C_d$) teorik değere **%0.7** yakınlıkta,
3. İtki kuvveti, basınç farkı etkisiyle teorik değerin üzerinde (**43.57 kN**) elde edilmiştir.

Bu durum, motorun yüksek basınç oranlarında çalışırken lüle çıkışındaki genişleme oranının ($A_9/A_8$) artırılması gerektiğini işaret etmektedir.
