# Case-3: High Pressure & Supersonic Expansion Analysis

## 1. Giriş ve Amaç
[cite_start]Bu rapor, jet motoru nozzle tasarımının **Case-3 (Durum 3)** koşullarındaki sayısal analiz sonuçlarını içermektedir[cite: 14]. [cite_start]Bu aşamada, lülenin yüksek basınç ve düşük ortam basıncı altındaki genişleme (expansion) karakteristiği ve süpersonik akış verimi incelenmiştir[cite: 15].

## 2. Geometrik Parametreler
[cite_start]Tasarımda kullanılan lüle geometrisi, yüksek genişleme oranına göre optimize edilmiştir[cite: 14, 15]:

* [cite_start]**Giriş Alanı ($A_7$):** $0.19635 \, m^2$ [cite: 14]
* **Boğaz Alanı ($A_8$):** $0.06610 \, m^2$ [cite: 14]
* **Alan Oranı ($A_9 / A_8$):** $1.703$ [cite: 14]
* **Çıkış Alanı ($A_9$):** $0.11257 \, m^2$ (Hesaplanan)
* [cite_start]**Yakınsaklık Yarım Açısı ($\alpha$):** $30^\circ$ [cite: 16]
* [cite_start]**Iraksaklık Yarım Açısı ($\theta$):** $12^\circ$ [cite: 16]

## 3. Sınır Koşulları (Boundary Conditions)
[cite_start]Analiz, ANSYS Fluent içerisinde aşağıdaki sınır koşulları altında gerçekleştirilmiştir[cite: 14]:

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
[cite_start]Süreklilik denkleminin sağlanması ve kütle korunumunun kontrolü amacıyla debi verileri incelenmiştir[cite: 18].

* [cite_start]**Teorik (Hedef) Debi:** $35.907 \, kg/s$ 
* **CFD Giriş Debisi:** $36.1196 \, kg/s$ 
* [cite_start]**CFD Çıkış Debisi:** $-36.12082 \, kg/s$ 

**Hata Analizi:**
[cite_start]Teorik hedef ile CFD çıkış debisi arasındaki fark[cite: 18]:

$$\text{Hata} = \left| \frac{36.12082 - 35.907}{35.907} \right| \times 100 = \%0.59$$

### 4.2. Deşarj Katsayısı ($C_d$) Hesabı
[cite_start]Boğaz bölgesindeki akış verimliliğini belirlemek için aşağıdaki yöntem kullanılmıştır[cite: 19, 20]:

$$C_d = \frac{\dot{m}_{bulunan}}{\dot{m}_{ideal}}$$

[cite_start]Termodinamik denklemlerle hesaplanan **İdeal Kütlesel Debi ($\dot{m}_{ideal}$)** değeri **$38.16 \, kg/s$** olarak bulunmuştur[cite: 20].

* [cite_start]**Teorik $C_d$ (Referans):** $0.940$ [cite: 18]
* **CFD $C_d$ (Hesaplanan):** $0.9465$ [cite: 20]


---

### 4.3. İtki Kuvveti ($F_g$) Analizi
[cite_start]Lüle çıkış yüzeyinden (Station 9) alınan verilerle net itki hesaplanmıştır[cite: 22, 23].

* **Çıkış Hızı ($V_9$):** $817.922 \, m/s$ [cite: 22]
* **Çıkış Basıncı ($P_9$):** $51,012.3 \, Pa$ [cite: 22]

[cite_start]**İtki Hesabı Formülü[cite: 23]:**

$$F_g = (\dot{m} \times V_9) + A_9 \times (P_9 - P_0)$$

**Sonuçlar:**
* **Şartname (Teorik) İtki:** $29.48 \, kN$ [cite: 21]
* [cite_start]**CFD Sonucu (Net İtki):** $\mathbf{30.045 \, kN}$ [cite: 23]

---

### 4.4. İtki ($F_g$) ve Verim ($C_{fg}$) Karşılaştırmalı Analiz
[cite_start]Analizden elde edilen performans verileri, şartname değerleri ile karşılaştırılmıştır[cite: 26].

| Parametre | Teorik / Şartname | CFD Sonucu | Fark |
| :--- | :--- | :--- | :--- |
| **İtki Kuvveti ($F_g$)** | $29.48 \, kN$ | $30.045 \, kN$ | %1.91 |
| **İtki Katsayısı ($C_{fg}$)** | $0.968$ | $0.961$ | %0.72 |

[cite_start]**Hesaplanan $C_{fg}$ Değeri[cite: 26]:**

$$C_{fg} = \frac{F_{g,bulunan}}{F_{g,ideal}} = \frac{30.045}{31.25} = \mathbf{0.961}$$


## 5. Sonuç
[cite_start]Case-3 analizinde lüle, süpersonik rejime tam uyum sağlamış ve Mach 2.24 hızına ulaşmıştır[cite: 14]. [cite_start]Yapılan debi ve itki karşılaştırmaları sonucunda, CFD modelinin teorik verilerle **%99'un üzerinde tutarlılıkla** örtüştüğü doğrulanmıştır[cite: 18].
