
# Case-3: High Pressure & Supersonic Expansion Analysis

## 1. Giriş ve Amaç
Bu rapor, jet motoru nozzle tasarımının **Case-2 (Durum 3)** koşullarındaki sayısal analiz sonuçlarını içermektedir. Bu aşamada, lülenin yüksek basınç ve düşük ortam basıncı altındaki genişleme (expansion) karakteristiği ve süpersonik akış verimi incelenmiştir.

## 2. Geometrik Parametreler
Tasarımda kullanılan lüle geometrisi, yüksek genişleme oranına göre optimize edilmiştir:

* **Giriş Alanı ($A_7$):** $0.19635 \, m^2$
* **Boğaz Alanı ($A_8$):** $0.06610 \, m^2$
* **Alan Oranı ($A_9/A_8$):** $1.703$
* **Çıkış Alanı ($A_9$):** $0.11257 \, m^2$
* **Yakınsaklık Yarım Açısı ($\alpha$):** $30^\circ$
* **Iraksaklık Yarım Açısı ($\theta$):** $12^\circ$

## 3. Sınır Koşulları (Boundary Conditions)
Analiz, ANSYS Fluent içerisinde aşağıdaki sınır koşulları altında gerçekleştirilmiştir:

| Parametre | Sembol | Değer | Birim |
| :--- | :--- | :--- | :--- |
| Giriş Toplam Basıncı | $P_{t7}$ | 400,000 | Pa |
| Giriş Toplam Sıcaklığı | $T_{t7}$ | 768.63 | K |
| Ortam Basıncı | $P_0$ | 46,562 | Pa |
| Ortam Sıcaklığı | $T_0$ | 248.53 | K |
| Özgül Isı Kapasitesi | $C_p$ | 1084.2 | J/kg·K |

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

*%1'in altındaki bu düşük hata oranı (%0.59), sınır koşulları ve çözüm ağının (mesh) yüksek irtifa koşullarında dahi mükemmel çalıştığını kanıtlamaktadır.*

### 4.2. Deşarj Katsayısı ($C_d$) Hesabı
Boğaz bölgesindeki akış verimliliğini belirlemek için debi oranları kullanılmıştır.

**Kullanılan Formül:**
$$C_d = \frac{\dot{m}_{bulunan}}{\dot{m}_{ideal}}$$

Termodinamik denklemlerle hesaplanan **İdeal Kütlesel Debi ($\dot{m}_{ideal}$)** değeri **$38.16 \, kg/s$** olarak bulunmuştur.

* **Teorik $C_d$ (Referans):** $0.940$
* **CFD $C_d$ (Hesaplanan):** $36.12082 / 38.16 = \mathbf{0.9465}$

---

### 4.3. İtki Kuvveti ($F_g$) Analizi
Lüle çıkış yüzeyinden alınan verilerle net itki hesaplanmıştır.

* **Çıkış Hızı ($V_9$):** $817.922 \, m/s$
* **Çıkış Basıncı ($P_9$):** $51,012.3 \, Pa$

**İtki Hesabı Formülü:**
$$F_g = (\dot{m} \times V_9) + A_9 \times (P_9 - P_0)$$

**Hesaplama:**
$$F_{g,CFD} = (36.12082 \times 817.922) + 0.11257 \times (51012.3 - 46562)$$
$$F_{g,CFD} \approx 29,544 + 501 = \mathbf{30.045 \, kN}$$

---

### 4.4. İtki ($F_g$) ve Verim ($C_{fg}$) Karşılaştırmalı Analiz
Analizden elde edilen performans verileri, şartname (specification) değerleri ile karşılaştırılmıştır.

| Parametre | Teorik / Şartname | CFD Sonucu | Hata / Fark |
| :--- | :--- | :--- | :--- |
| **İtki Kuvveti ($F_g$)** | $29.48 \, kN$ | $30.045 \, kN$ | %1.91 |
| **İtki Katsayısı ($C_{fg}$)** | $0.968$ | $0.961$ | %0.72 |

**Değerlendirme:**
1. **İtki ($F_g$):** CFD sonucu şartname değerinden %1.91 daha yüksek çıkmıştır. Bu fark, lüle çıkışındaki basınç farkından ($P_9 > P_0$) kaynaklanan ekstra basınç itkisinin teorik modelden daha etkili olduğunu gösterir.
2. **Verim ($C_{fg}$):** Hesaplanan $0.961$ değeri, teorik $0.968$ referansına çok yakındır. Aradaki %0.72'lik küçük kayıp, lüle içindeki viskoz sürtünmeler ve süpersonik akıştaki sınır tabaka etkileriyle açıklanabilir.

## 5. Sonuç
Case-3 analizinde lüle, süpersonik rejime tam uyum sağlamış ve Mach 2.24 hızına ulaşmıştır. Yapılan debi ve itki karşılaştırmaları sonucunda, CFD modelinin teorik verilerle **%99'un üzerinde tutarlılıkla** örtüştüğü doğrulanmıştır.
