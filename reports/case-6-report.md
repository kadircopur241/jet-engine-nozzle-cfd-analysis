# Case 6: Lüle (Nozzle) Akış Analizi Raporu

Bu rapor, belirlenen geometrik ve termodinamik sınır koşulları altında, süpersonik bir lülenin akış karakteristiklerinin ANSYS Fluent kullanılarak yapılan CFD analiz sonuçlarını ve teorik karşılaştırmalarını içermektedir.

## 1. Analiz Sınır Koşulları ve Geometri

Analizlerde kullanılan temel sınır koşulları ve geometrik parametreler aşağıda özetlenmiştir:

* **Giriş Basıncı ($P_{in}$):** $160,000$ Pa
* **Giriş Sıcaklığı ($T_{in}$):** $788.24$ K
* **Ortam Basıncı ($P_{amb}$):** $7171$ Pa
* **Ortam Sıcaklığı ($T_{amb}$):** $216.65$ K
* **Özgül Isı ($c_p$):** $1084.2$ J/kgK
* **Geometri:**
    * Giriş Alanı: $0.19635$ $m^2$
    * Boğaz Alanı ($A_t$): $0.06683$ $m^2$
    * Alan Oranı ($A_e / A_t$): $2.000$
    * Yakınsaklık / Iraksaklık Açısı: $30^\circ$ / $12^\circ$

---

## 2. Kütlesel Debi ve Süreklilik Analizi

Süreklilik ilkesinin sağlanıp sağlanmadığını kontrol etmek amacıyla giriş ve çıkış kütlesel debileri kıyaslanmıştır:

* **Teorik Kütlesel Debi:** $14.430$ kg/s
* **Analiz (CFD) Giriş Debisi:** $14.43458$ kg/s
* **Analiz (CFD) Çıkış Debisi:** $14.43422$ kg/s

### Hata Analizi
Teorik değer ile analiz sonucu arasındaki sapma aşağıdaki gibi hesaplanmıştır:

$$\%Hata = \left| \frac{\dot{m}_{CFD} - \dot{m}_{teorik}}{\dot{m}_{teorik}} \right| \times 100$$

$$\%Hata = \left| \frac{14.43422 - 14.430}{14.430} \right| \times 100 = \mathbf{\%0.029}$$

---

## 3. Akış Katsayısı ($C_d$)

Akış katsayısı, lülenin gerçek debi geçirme kapasitesinin ideal duruma oranıdır. Boğaz alanındaki sonik hattın tespiti zor olduğundan, debi oranları kullanılmıştır:

$$C_d = \frac{\dot{m}_{bulunan}}{\dot{m}_{ideal}}$$

Bu denklem ve kabul ile elde edilen sonuçlar:
* **Teorik $C_d$:** $0.941$
* **Hesaplanan $C_d$:** $0.956$

---

## 4. İdeal Akış Parametreleri (İsentropik Kabuller)

İtki performansını değerlendirmek için ideal koşullardaki kütlesel debi ve çıkış hızı termodinamik bağıntılarla hesaplanmıştır.

### İdeal Kütlesel Debi ($\dot{m}_{ideal}$) Formülü
Kritik (boğaz) koşullarında kütlesel debi bağıntısı:

$$\dot{m}_{ideal} = \frac{P_0 A^*}{\sqrt{T_0}} \sqrt{\frac{\gamma}{R}} \left( \frac{2}{\gamma+1} \right)^{\frac{\gamma+1}{2(\gamma-1)}}$$

* Bu denklem sonucunda referans alınan değer: **$15.239$ kg/s**

### İdeal Çıkış Hızı ($V_{ideal}$) Formülü
Lülenin izentropik olarak ortam basıncına genişlediği varsayıldığında ideal çıkış hızı:

$$V_{ideal} = \sqrt{2 c_p (T_0 - T_e)} \quad \text{veya} \quad V_{ideal} = \sqrt{\frac{2\gamma R T_0}{\gamma-1} \left[ 1 - \left( \frac{P_e}{P_0} \right)^{\frac{\gamma-1}{\gamma}} \right]}$$

* Yukarıdaki denklemler yardımıyla bulunan değer: **$942.292$ m/s**

---

## 5. İtki Kuvveti ($F_g$) ve İtki Katsayısı ($C_{fg}$)

### İtki Kuvveti Hesabı
Analizden elde edilen çıkış verileri ($V_e = 872.968$ m/s, $P_e = 15405.2$ Pa) kullanılarak itki kuvveti hesaplanmıştır:

$$F_g = (\dot{m} \cdot V_e) + A_e (P_e - P_a)$$

* **Verilen İtki:** $13.35$ kN
* **Hesaplanan İtki ($F_{g, bulunan}$):** $13.70$ kN

### İtki Katsayısı ($C_{fg}$)
Gerçek itkinin ideal itkiye oranıdır:

$$C_{fg} = \frac{F_{g, bulunan}}{F_{g, ideal}} = \frac{F_{g, bulunan}}{\dot{m}_{ideal} \cdot V_{ideal}}$$

$$F_{g, ideal} = 15.239 \times 942.292 \approx 14.36 \text{ kN}$$

* **Teorik $C_{fg}$:** $0.956$
* **Hesaplanan $C_{fg}$:** $0.954$

---

## 6. Sonuç ve Değerlendirme

Yapılan CFD analizleri ve teorik hesaplamaların karşılaştırılması sonucunda aşağıdaki çıkarımlar yapılmıştır:

1.  **Sayısal Doğruluk:** Kütlesel debi korunumunda elde edilen **%0.029** gibi çok düşük hata oranı, kurulan sayısal modelin ve sınır koşullarının fiziksel gerçeklikle yüksek derecede örtüştüğünü ve çözümün yakınsadığını (convergence) göstermektedir.
2.  **Performans Katsayıları:** Hesaplanan itki katsayısı ($C_{fg} = 0.954$) ile teorik değer ($0.956$) arasındaki farkın binde 2 seviyesinde olması, lülenin momentum üretimi ve basınç geri kazanımı açısından tasarım hedeflerini tam olarak karşıladığını kanıtlar.
3.  **Akış Fiziği:** Mach
