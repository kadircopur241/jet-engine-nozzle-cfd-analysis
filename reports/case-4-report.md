# Case-5: High Supersonic Expansion & Performance Validation

## 1. Giriş ve Amaç
Bu rapor, lüle tasarımının **Case-5 (Durum 5)** koşullarındaki sayısal analiz sonuçlarını içermektedir. Bu aşamada, belirlenen basınç farkı altında lülenin süpersonik deşarj kapasitesi ve elde edilen itki kuvvetinin teorik değerlerle doğrulanması amaçlanmıştır.

## 2. Geometrik Parametreler
Tasarımda kullanılan lüle geometrisi, belirlenen Mach sayısı hedeflerine ulaşmak için optimize edilmiş yakınsak-ıraksak bir yapıdır:

* **Giriş Alanı ($A_7$):** $0.19635 \, m^2$
* **Boğaz Alanı ($A_8$):** $0.06645 \, m^2$
* **Alan Oranı ($A_9 / A_8$):** $2.000$
* **Çıkış Alanı ($A_9$):** $0.1329 \, m^2$
* **Yakınsaklık Yarım Açısı ($\alpha$):** $30^\circ$
* **Iraksaklık Yarım Açısı ($\theta$):** $12^\circ$

![Mesh Görünümü](case-5-mesh.png)
*Şekil 1: Mesh Ortogonal Kalite Dağılımı*

## 3. Sınır Koşulları (Boundary Conditions)
Analiz, ANSYS Fluent içerisinde aşağıdaki sınır koşulları altında gerçekleştirilmiştir. Akışkan olarak İdeal Gaz (Hava) seçilmiş olup, özgül ısı kapasitesi ($C_p$) sabit $1084.2 \, J/kgK$ kabul edilmiştir.

| Parametre | Sembol | Değer | Birim |
| :--- | :--- | :--- | :--- |
| Giriş Basıncı | $P_{in}$ | 210,000 | Pa |
| Giriş Sıcaklığı | $T_{in}$ | 776.47 | K |
| Ortam Basıncı | $P_{amb}$ | 11,597 | Pa |
| Ortam Sıcaklığı | $T_{amb}$ | 216.65 | K |

---

## 4. Performans Analizi ve Doğrulama

### 4.1. Kütlesel Debi Analizi ($\dot{m}$)
Süreklilik denkleminin sağlanması amacıyla giriş ve çıkış kütlesel debileri incelenmiştir.

* **Teorik (Hedef) Debi:** $18.857 \, kg/s$
* **CFD Giriş Debisi:** $18.97863 \, kg/s$
* **CFD Çıkış Debisi:** $-18.97797 \, kg/s$ (Net akış)

**Hata Analizi:**

$$
\text{Hata} = \left| \frac{18.978 - 18.857}{18.857} \right| \times 100 \approx \%0.64
$$

*%1'in altındaki bu sapma, çözüm ağının ve termodinamik modelin tutarlılığını göstermektedir.*

### 4.2. Deşarj Katsayısı ($C_d$) Hesabı
Boğaz bölgesindeki akış verimliliğini belirlemek için Mach sayısının 1 olduğu bölgenin tespiti yerine kütlesel debi oranı yöntemi kullanılmıştır:

$$
C_d = \frac{\dot{m}_{bulunan}}{\dot{m}_{ideal}}
$$

Termodinamik denklemlerle hesaplanan **İdeal Kütlesel Debi ($\dot{m}_{ideal}$)** değeri **$20.03859 \, kg/s$** olarak bulunmuştur.

* **Teorik $C_d$ (Referans):** $0.940$
* **CFD $C_d$ (Hesaplanan):** $18.97863 / 20.03859 = \mathbf{0.956}$

---

### 4.3. İtki Kuvveti ($F_g$) Analizi
Lüle çıkış yüzeyinden alınan güncel verilerle net itki hesaplanmıştır. Mach sayısı dağılımı ve basınç konturları aşağıda sunulmuştur.

![Mach Sayısı](case-5-mach-number.png)
*Şekil 2: Mach Sayısı Dağılımı*

![Basınç Dağılımı](case-5-pressure.png)
*Şekil 3: Statik Basınç Dağılımı*

* **Çıkış Hızı ($V_9$):** $876.89 \, m/s$
* **Çıkış Mutlak Basıncı ($P_9$):** $20,213.8 \, Pa$

**İtki Hesabı Formülü:**

$$
F_g = (\dot{m} \times V_9) + A_9 \times (P_9 - P_0)
$$

**Hesaplama:**

$$
F_{g,CFD} = (18.97797 \times 876.89) + 0.1329 \times (20213.8 - 11597)
$$

$$
F_{g,CFD} \approx 16,641 + 1,145 = \mathbf{17.786 \, kN}
$$

---

### 4.4. İtki ($F_g$) ve Verim ($C_{fg}$) Karşılaştırmalı Analiz
Analiz verileri ile teorik referanslar arasındaki ilişki karşılaştırılmıştır. İdeal itki kuvveti ($F_{g, ideal}$) termodinamik denklemlerle **18.318 kN** olarak hesaplanmıştır.

| Parametre | Teorik / Şartname | CFD Sonucu |
| :--- | :--- | :--- |
| **İtki Kuvveti ($F_g$)** | $18.318 \, kN$ (İdeal) | $17.786 \, kN$ |
| **İtki Katsayısı ($C_{fg}$)** | $0.961$ | $0.971$ |

**İtki Katsayısı ($C_{fg}$) Hesabı:**

$$
C_{fg} = \frac{F_{g,bulunan}}{F_{g,ideal}} = \frac{17.786}{18.318} = \mathbf{0.971}
$$

**Değerlendirme:**
* **İtki:** CFD sonucu, ideal itki değerine oldukça yakındır.
* **Verim:** Hesaplanan $0.971$ $C_{fg}$ değeri, teorik referans olan $0.961$ değerine oldukça yakındır ve lülenin yüksek performansla çalıştığını kanıtlar.

## 5. Sonuç ve Genel Değerlendirme
Case-5 analizleri, lülenin yüksek genişleme rejiminde stabil ve yüksek verimli çalıştığını göstermiştir.

1. **Süreklilik:** Kütlesel debi dengesi yüksek hassasiyetle sağlanmıştır.
2. **Hassasiyet:** Deşarj katsayısı ve itki verimi teorik beklentilerle uyumludur.
3. **Doğrulama:** Tasarlanan geometri, verilen basınç ve sıcaklık koşullarında hedef performans kriterlerini karşılamaktadır.
