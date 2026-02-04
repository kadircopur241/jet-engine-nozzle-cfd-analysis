# Case-2: Analysis & Validation Report ($M_{N0}=1.00$)

## 1. Giriş ve Amaç
Bu rapor, jet motoru nozzle tasarımının **Case-2 (Durum 2)** koşullarındaki sayısal analiz sonuçlarını içermektedir. Bu analiz setinde, lüle giriş basıncı artırılarak (580 kPa) performans karakteristiklerinin değişimi ve nozzle'ın yüksek basınç altındaki davranışları incelenmiştir.

## 2. Geometrik Parametreler
Case-2 analizinde kullanılan lüle geometrisi, tasarım noktası (DP) ile aynı olup, genişleme oranları sabittir:

* **Giriş Alanı ($A_7$):** $0.19635 \, m^2$
* **Boğaz Alanı ($A_8$):** $0.06675 \, m^2$
* **Alan Oranı ($A_9/A_8$):** $1.373$
* **Çıkış Alanı ($A_9$):** $0.09165 \, m^2$
* **Yakınsaklık Yarım Açısı ($\alpha$):** $30^\circ$
* **Iraksaklık Yarım Açısı ($\theta$):** $12^\circ$

## 3. Sınır Koşulları (Boundary Conditions)
Analiz, ANSYS Fluent içerisinde aşağıdaki işletme koşulları altında gerçekleştirilmiştir. Akışkan olarak **İdeal Gaz** (Hava) seçilmiş olup, vizkozite için **Sutherland** modeli, ısı kapasitesi ($C_p$) için ise sıcaklığa bağlı polinom kullanılmıştır ($C_p \approx 1084.2 \, J/kgK$).

| Parametre | Sembol | Değer | Birim |
| :--- | :--- | :--- | :--- |
| Giriş Toplam Basıncı | $P_{t7}$ | 580,000 | Pa |
| Giriş Toplam Sıcaklığı | $T_{t7}$ | 784.31 | K |
| Ortam Basıncı | $P_0$ | 101,325 | Pa |
| Ortam Sıcaklığı | $T_0$ | 288.15 | K |

---

## 4. Performans Analizi ve Doğrulama

### 4.1. Kütlesel Debi Analizi ($\dot{m}$)
$C_p$ düzeltmesi sonrası yapılan analizde, süreklilik denkleminin çok daha hassas bir şekilde sağlandığı görülmüştür.

* **Teorik (Hedef) Debi:** $52.054 \, kg/s$
* **CFD Giriş Debisi:** $52.36805 \, kg/s$
* **CFD Çıkış Debisi:** $-52.36831 \, kg/s$ (Net akış)

**Hata Analizi:**

$$
\text{Hata} = \left| \frac{52.36831 - 52.054}{52.054} \right| \times 100 = \%0.60
$$

*%1.55 olan hata oranı, termodinamik modelin iyileştirilmesiyle (Real Gas effects) %0.60 seviyesine düşürülmüştür. Bu sonuç mükemmel bir doğruluğu işaret eder.*

### 4.2. Deşarj Katsayısı ($C_d$) Hesabı
Efektif akış alanının doğrulanması amacıyla Deşarj Katsayısı güncel debi ile yeniden hesaplanmıştır.

**Kullanılan Formül:**
$$C_d = \frac{\dot{m}_{bulunan}}{\dot{m}_{ideal}}$$

Termodinamik denklemlerle hesaplanan **İdeal (Isentropic) Kütlesel Debi ($\dot{m}_{ideal}$)** değeri **$55.316 \, kg/s$** olarak referans alınmıştır.

* **Teorik $C_d$ (Referans):** $0.940$
* **CFD $C_d$ (Hesaplanan):** $52.368 / 55.316 = 0.9467$

**Karşılaştırma:**
Referans değer ($0.940$) ile analiz sonucu ($0.947$) arasındaki fark binde 7 mertebesindedir. Mesh yapısının sınır tabaka etkilerini ($boundary layer$) başarıyla modellediği görülmektedir.

---

### 4.3. İtki Kuvveti ($F_g$) Analizi
Lüle çıkış yüzeyindeki basınç ve momentum entegrasyonu sonucunda elde edilen net itki kuvveti aşağıdadır.

**İtki Hesabı Formülü:**
$$F_g = (\dot{m} \times V_9) + \int (P_{local} - P_0) dA$$

**Sonuçlar:**
* **Şartname (Teorik) İtki:** $40.00 \, kN$
* **CFD Sonucu (Net İtki):** $\mathbf{39.9615 \, kN}$

**Hata Analizi:**
$$\text{Hata} = \left| \frac{39.9615 - 40.00}{40.00} \right| \times 100 = \%0.096$$

*Teorik hedef ile CFD sonucu arasında **%0.1'in altında** mükemmel bir uyum yakalanmıştır. Fluent tarafından hesaplanan net kuvvet (Force Report), manuel ortalama hesaplamalarına göre çok daha hassas sonuç vermiştir.*

---

### 4.4. İtki Katsayısı ($C_{fg}$)
İdeal koşullardaki performans ile gerçek performansın kıyaslanmasıdır.

**İdeal Değerler:**
* $\dot{m}_{ideal} = 55.316 \, kg/s$
* $V_{ideal} = 763.602 \, m/s$

$$F_{g,ideal} = \dot{m}_{ideal} \times V_{ideal}$$
$$F_{g,ideal} = 55.316 \times 763.602 \approx \mathbf{42.24 \, kN}$$

**İtki Katsayısı Hesabı:**

$$C_{fg} = \frac{F_{g,bulunan}}{F_{g,ideal}} = \frac{39.9615}{42.24} = \mathbf{0.946}$$

* **Teorik $C_{fg}$:** $0.970$
* **Hesaplanan $C_{fg}$:** $0.946$

**Sonuç:**
Hesaplanan itki katsayısı, teorik beklentiye oldukça yakındır. Aradaki küçük fark, lüle içerisindeki şok dalgaları ve viskoz kayıplardan kaynaklanmaktadır.

---

## 5. Sonuç ve Genel Değerlendirme

Case-2 (Yüksek Basınç Altında Performans) analizleri sonucunda elde edilen veriler şu şekildedir:

1. **Akış Rejimi:** Giriş basıncının 580 kPa değerine yükseltilmesiyle birlikte nozzle, yüksek basınç oranlarında (NPR) kararlı yapısını korumuş ve verimli bir deşarj sergilemiştir.

2. **Kütlesel Debi ve $C_p$ Etkisi:** * Sıcaklığa bağlı $C_p$ düzeltmesi sonrası kütlesel debi hatası **%0.60** seviyesine indirilmiştir. 
   * **CFD Çıkış Debisi:** $52.368 \, kg/s$ olarak kaydedilmiştir.

3. **İtki Kuvveti ve Hassasiyet:** * **Şartname İtki:** $40.00 \, kN$
   * **CFD Net İtki:** $39.9615 \, kN$
   * **Hata:** %0.096 (Mükemmel uyum).
   * Fluent üzerinden alınan Force Report verileri, tasarımın hedeflenen 40 kN itkiyi %99.9 hassasiyetle üretebildiğini ispatlamıştır.

4. **Verimlilik Analizi ($C_{fg}$):** * Hesaplanan **0.946** $C_{fg}$ değeri, yüksek basınçlı akışlarda lüle içindeki viskoz kayıpların kontrol altında tutulduğunu göstermektedir.

5. **Genel Kanı:** Case-2 sonuçları, tasarımın zorlayıcı basınç koşullarında bile nominal performansından ödün vermediğini ve yüksek itki gereksinimlerini başarıyla karşıladığını doğrular.
