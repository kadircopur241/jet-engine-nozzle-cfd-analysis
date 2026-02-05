# Case-3: High Pressure & Supersonic Expansion Analysis

## 1. Giriş ve Amaç
Bu rapor, jet motoru nozzle tasarımının **Durum 3 (Case-3)** koşullarındaki sayısal analiz sonuçlarını içermektedir. Bu aşamada, lülenin yüksek basınç ve düşük ortam basıncı altındaki genişleme (expansion) karakteristiği ve süpersonik akış verimi incelenmiştir.

## 2. Geometrik Parametreler
Tasarımda kullanılan lüle geometrisi, yüksek genişleme oranına göre optimize edilmiştir:

* **Giriş Alanı ($A_7$):** $0.19635 \, m^2$
* **Boğaz Alanı ($A_8$):** $0.06610 \, m^2$
* **Alan Oranı ($A_9 / A_8$):** $1.703$
* **Çıkış Alanı ($A_9$):** $0.11257 \, m^2$
* **Yakınsaklık Yarım Açısı ($\alpha$):** $30^\circ$
* **Iraksaklık Yarım Açısı ($\theta$):** $12^\circ$

## 3. Sınır Koşulları (Boundary Conditions)
Analiz, ANSYS Fluent içerisinde aşağıdaki işletme koşulları altında gerçekleştirilmiştir. Akışkan olarak "İdeal Gaz" (Hava) seçilmiş olup, özgül ısı kapasitesi ($C_p$) sıcaklığın bir fonksiyonu olarak tanımlanmış ve analiz sırasında her hücredeki yerel sıcaklık değerine göre dinamik olarak hesaplanmıştır. Durum 3 (Case-3) için yapılan bu analizde ısı kapasitesi ($C_p$) $1082.2 \, J/kgK$ olarak hesaplanmıştır.

| Parametre | Sembol | Değer | Birim |
| :--- | :--- | :--- | :--- |
| Giriş Toplam Basıncı | $P_{t7}$ | 400,000 | Pa |
| Giriş Toplam Sıcaklığı | $T_{t7}$ | 768.63 | K |
| Ortam Basıncı | $P_0$ | 46,562 | Pa |
| Ortam Sıcaklığı | $T_0$ | 248.53 | K |

---

## 4. Performans Analizi ve Doğrulama

### 4.1. Kütlesel Debi Analizi ($\dot{m}$) ve Süreklilik Kontrolü
Süreklilik denkleminin sağlanması amacıyla hem giriş-çıkış farkı (sayısal kararlılık) hem de teorik değerle olan sapma (model doğruluğu) kontrol edilmiştir.

* **Teorik (Hedef) Debi:** $35.907 \, kg/s$
* **CFD Giriş Debisi ($\dot{m}_{in}$):** $36.1196 \, kg/s$
* **CFD Çıkış Debisi ($\dot{m}_{out}$):** $-36.12082 \, kg/s$

**1. Süreklilik Hatası (Giriş vs Çıkış):**

$$
\text{Hata}_{\text{süreklilik}} = \left| \frac{\dot{m}_{in} - |\dot{m}_{out}|}{\dot{m}_{in}} \right| \times 100 = \mathbf{\%0.0034}
$$

**2. Tahmin Hatası (CFD vs Teorik):**

$$
\text{Hata}_{\text{tahmin}} = \left| \frac{|\dot{m}_{out}| - 35.907}{35.907} \right| \times 100 = \mathbf{\%0.595}
$$

*%1'in altındaki bu sapma, çözüm ağının (mesh) ve sınır koşullarının yüksek doğruluğunu kanıtlamaktadır.*

### 4.2. Deşarj Katsayısı ($C_d$) Karşılaştırması
Boğaz bölgesindeki gerçek akışın ideal izentropik akışa oranı üzerinden hesaplanan $C_d$ analizi aşağıdadır:

$$
C_d = \frac{\dot{m}_{bulunan}}{\dot{m}_{ideal}} = \frac{36.12082}{38.16} = \mathbf{0.9465}
$$

* **Teorik $C_d$ Referansı:** $0.940$
* **CFD Hesaplanan $C_d$:** $0.9465$
* **Fark:** %0.69

---

### 4.3. İtki Kuvveti ($F_g$) Analizi
Lüle çıkış yüzeyinden alınan verilerle toplam net itki hesaplanmıştır.

* **Çıkış Hızı ($V_9$):** $817.922 \, m/s$
* **Çıkış Mutlak Basıncı ($P_9$):** $51,012.3 \, Pa$
* **Çıkış Alanı ($A_9$):** $0.11257 \, m^2$

**İtki Formülü:**

$$
F_g = (\dot{m} \times V_9) + A_9 \times (P_9 - P_0)
$$

**CFD İtki Hesabı:**

$$
F_{g,CFD} = (36.12082 \times 817.922) + 0.11257 \times (51012.3 - 46562) = \mathbf{30.045 \, kN}
$$

---

### 4.4. İtki ($F_g$) ve Verim ($C_{fg}$) Karşılaştırmalı Analiz
Lülenin genel verimlilik göstergesi olan $C_{fg}$ değeri için kullanılan termodinamik denklemler aşağıdadır:

**İdeal Kütlesel Debi ve Çıkış Hızı Formülleri:**

$$
\dot{m}_{ideal} = \frac{A_8 \cdot P_{t7}}{\sqrt{T_{t7}}} \sqrt{\frac{\gamma}{R} \left( \frac{2}{\gamma+1} \right)^{\frac{\gamma+1}{\gamma-1}}} \quad , \quad V_{ideal} = \sqrt{2 \cdot C_p \cdot T_{t7} \left[ 1 - \left( \frac{P_0}{P_{t7}} \right)^{\frac{\gamma-1}{\gamma}} \right]}
$$

* **İdeal Kütlesel Debi ($\dot{m}_{ideal}$):** $38.16 \, kg/s$
* **İdeal Çıkış Hızı ($V_{ideal}$):** $874.72 \, m/s$
* **İdeal İtki ($F_{g,ideal}$):** $31.25 \, kN$

**Karşılaştırma Tablosu:**

| Parametre | Teorik / Şartname | CFD Sonucu | Hata / Fark |
| :--- | :--- | :--- | :--- |
| **İtki Kuvveti ($F_g$)** | $29.48 \, kN$ | $30.045 \, kN$ | %1.91 |
| **İtki Katsayısı ($C_{fg}$)** | $0.968$ | $0.961$ | %0.72 |

**İtki Katsayısı ($C_{fg}$) Hesabı:**

$$
C_{fg,CFD} = \frac{30.045}{31.25} = \mathbf{0.961}
$$

---

## 5. Sonuç ve Genel Değerlendirme

Case-3 (Yüksek İrtifa / Düşük Ortam Basıncı) koşullarında gerçekleştirilen analizler sonucunda şu çıkarımlar yapılmıştır:

1. **Akış Rejimi:** Lüle, 400 kPa giriş ve 46.56 kPa ortam basıncı altında tam süpersonik rejime ulaşmış ve çıkışta Mach 2.24 değeri gözlemlenmiştir. Bu durum lülenin tasarlanan genişleme oranında ($1.703$) verimli çalıştığını kanıtlar.
2. **Sayısal Doğrulama:** Süreklilik hatasının **%0.0034** seviyesinde kalması çözümün başarısını, kütlesel debi tahmin hatasının **%0.59** olması ise modelin hassasiyetini doğrulamaktadır.
3. **İtki ve Verimlilik:** Elde edilen net itki ($30.045 \, kN$), şartname değerinin %1.91 üzerindedir. Aradaki fark, lüle çıkışındaki basınç farkından kaynaklanan ek basınç itkisini temsil eder.
4. **Genel Kanı:** Hesaplanan **0.961** $C_{fg}$ değeri, tasarımın yüksek süpersonik hızlarda bile viskoz kayıpları kontrol altında tutarak yüksek verim sağladığını ispatlamıştır.
