# Case-3: High Pressure & Supersonic Expansion Analysis

## 1. Giriş ve Amaç
Bu rapor, jet motoru nozzle tasarımının **Case-3 (Durum 3)** koşullarındaki sayısal analiz sonuçlarını içermektedir. Bu aşamada, lülenin yüksek basınç ve düşük ortam basıncı altındaki genişleme (expansion) karakteristiği ve süpersonik akış verimi incelenmiştir.

## 2. Geometrik Parametreler
Tasarımda kullanılan lüle geometrisi, yüksek genişleme oranına göre optimize edilmiştir:

* **Giriş Alanı ($A_7$):** $0.19635 \, m^2$
* **Boğaz Alanı ($A_8$):** $0.06610 \, m^2$
* **Alan Oranı ($A_9 / A_8$):** $1.703$
* **Çıkış Alanı ($A_9$):** $0.11257 \, m^2$
* **Yakınsaklık Yarım Açısı ($\alpha$):** $30^\circ$
* **Iraksaklık Yarım Açısı ($\theta$):** $12^\circ$

## 3. Sınır Koşulları (Boundary Conditions)
Analiz, ANSYS Fluent içerisinde aşağıdaki sınır koşulları altında gerçekleştirilmiştir. Akışkan olarak İdeal Gaz (Hava) seçilmiş olup, özgül ısı kapasitesi ($C_p$) sabit $1084.2 \, J/kgK$ kabul edilmiştir.

| Parametre | Sembol | Değer | Birim |
| :--- | :--- | :--- | :--- |
| Giriş Toplam Basıncı | $P_{t7}$ | 400,000 | Pa |
| Giriş Toplam Sıcaklığı | $T_{t7}$ | 768.63 | K |
| Ortam Basıncı | $P_0$ | 46,562 | Pa |
| Ortam Sıcaklığı | $T_0$ | 248.53 | K |

---

## 4. Performans Analizi ve Doğrulama

### 4.1. Kütlesel Debi Analizi ($\dot{m}$)
Süreklilik denkleminin sağlanması ve kütle korunumunun kontrolü amacıyla debi verileri incelenmiştir.

* **Teorik (Hedef) Debi:** $35.907 \, kg/s$
* **CFD Giriş Debisi:** $36.1196 \, kg/s$
* **CFD Çıkış Debisi:** $-36.12082 \, kg/s$ (Net akış)

**Hata Analizi:**

$$
\text{Hata} = \left| \frac{36.12082 - 35.907}{35.907} \right| \times 100 = \%0.59
$$

*%1'in altındaki bu hata oranı, çözüm ağının (mesh) ve sınır koşullarının doğruluğunu kanıtlamaktadır.*

### 4.2. Deşarj Katsayısı ($C_d$) Hesabı
Boğaz bölgesindeki akış verimliliğini belirlemek için aşağıdaki yöntem kullanılmıştır:

$$
C_d = \frac{\dot{m}_{bulunan}}{\dot{m}_{ideal}}
$$

Termodinamik denklemlerle hesaplanan **İdeal Kütlesel Debi ($\dot{m}_{ideal}$)** değeri **$38.16 \, kg/s$** olarak bulunmuştur.

* **Teorik $C_d$ (Referans):** $0.940$
* **CFD $C_d$ (Hesaplanan):** $36.12082 / 38.16 = \mathbf{0.9465}$

---

### 4.3. İtki Kuvveti ($F_g$) Analizi
Lüle çıkış yüzeyinden alınan verilerle net itki hesaplanmıştır.

* **Çıkış Hızı ($V_9$):** $817.922 \, m/s$
* **Çıkış Basıncı ($P_9$):** $51,012.3 \, Pa$

**İtki Hesabı Formülü:**

$$
F_g = (\dot{m} \times V_9) + A_9 \times (P_9 - P_0)
$$

**Sonuçlar:**
* **Şartname (Teorik) İtki:** $29.48 \, kN$
* **CFD Sonucu (Net İtki):** $\mathbf{30.045 \, kN}$

---

### 4.4. İtki ($F_g$) ve Verim ($C_{fg}$) Karşılaştırmalı Analiz
Analizden elde edilen performans verileri ile teorik referanslar arasındaki ilişki aşağıda özetlenmiştir.

| Parametre | Teorik / Şartname | CFD Sonucu | Hata / Fark |
| :--- | :--- | :--- | :--- |
| **İtki Kuvveti ($F_g$)** | $29.48 \, kN$ | $30.045 \, kN$ | %1.91 |
| **İtki Katsayısı ($C_{fg}$)** | $0.968$ | $0.961$ | %0.72 |

**İtki Katsayısı ($C_{fg}$) Hesabı:**

$$
C_{fg} = \frac{F_{g,bulunan}}{F_{g,ideal}} = \frac{30.045}{31.25} = \mathbf{0.961}
$$

**Değerlendirme:**
* **İtki:** CFD sonucu şartname değerinden %1.91 daha yüksek çıkmıştır. Bu durum, çıkış basıncının ortam basıncından yüksek olması ($P_9 > P_0$) nedeniyle oluşan ek basınç itkisinden kaynaklanır.
* **Verim:** Hesaplanan $0.961$ değeri, teorik $0.968$ referansına

---

## 5. Sonuç ve Genel Değerlendirme

Case-3 (Yüksek İrtifa / Düşük Ortam Basıncı) koşullarında gerçekleştirilen CFD analizleri sonucunda aşağıdaki teknik çıkarımlar yapılmıştır:

1. **Akış Rejimi:** Lüle, 400 kPa giriş ve 46.56 kPa ortam basıncı altında tam süpersonik rejime ulaşmış ve çıkışta **Mach 2.24** değeri gözlemlenmiştir. Bu durum, lülenin tasarlanan genişleme oranında ($1.703$) verimli çalıştığını kanıtlar.
   
2. **Kütlesel Debi Doğrulaması:** Teorik hedef olan $35.907 \, kg/s$ değeri ile CFD çıkış debisi ($36.12 \, kg/s$) arasındaki hata payı **%0.59** olarak gerçekleşmiştir. Bu düşük hata oranı, $C_p$ düzeltmesi ve mesh hassasiyetinin doğruluğunu teyit etmektedir.

3. **İtki ve Verimlilik:** * Elde edilen net itki ($30.045 \, kN$), şartname değerinin ($29.48 \, kN$) yaklaşık **%1.91** üzerindedir. 
   * İtki katsayısının **0.961** olarak hesaplanması, lülenin ideal (izentropik) duruma göre oldukça yüksek bir verimlilikle çalıştığını, kayıpların sınır tabaka ve viskoz etkilerle sınırlı kaldığını gösterir.

4. **Kıyaslama Özeti:**
   * **Hedef İtki:** $29.48 \, kN$ | **CFD İtki:** $30.045 \, kN$
   * **Hedef $C_{fg}$:** $0.968$ | **CFD $C_{fg}$:** $0.961$

Sonuç olarak; tasarlanan CD lüle geometrisi, Case-3 sınır koşulları altında kararlı bir süpersonik akış sağlamakta ve teorik performans kriterlerini **%99 mertebesinde** karşılamaktadır. Sayısal modelin (CFD) doğruluğu, literatürdeki teorik yaklaşımlarla tam uyum içerisindedir.
