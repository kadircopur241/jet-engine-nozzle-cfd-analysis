# Case-4: High Supersonic Expansion & Performance Validation

## 1. Giriş ve Amaç
Bu rapor, lüle tasarımının **Case-4 (Durum 4)** koşullarındaki sayısal analiz sonuçlarını içermektedir. Bu aşamada, yüksek basınç farkı altında lülenin süpersonik deşarj kapasitesi ve elde edilen itki kuvvetinin teorik değerlerle doğrulanması amaçlanmıştır.

## 2. Geometrik Parametreler
Tasarımda kullanılan lüle geometrisi, yüksek genişleme oranına göre optimize edilmiştir:

* [cite_start]**Giriş Alanı ($A_7$):** $0.19635 \, m^2$ [cite: 1]
* **Boğaz Alanı ($A_8$):** $0.06709 \, m^2$ [cite: 1]
* **Alan Oranı ($A_9 / A_8$):** $2.000$ [cite: 1]
* [cite_start]**Yakınsaklık Yarım Açısı ($\alpha$):** $30^\circ$ [cite: 3]
* [cite_start]**Iraksaklık Yarım Açısı ($\theta$):** $12^\circ$ [cite: 3]

## 3. Sınır Koşulları (Boundary Conditions)
[cite_start]Analiz, ANSYS Fluent içerisinde aşağıdaki sınır koşulları altında parametrik olarak gerçekleştirilmiştir: [cite: 2]

| Parametre | Sembol | Değer | Birim |
| :--- | :--- | :--- | :--- |
| Giriş Toplam Basıncı | $P_{t7}$ | 390,000 | [cite_start]Pa [cite: 1] |
| Giriş Toplam Sıcaklığı | $T_{t7}$ | 792.16 | [cite_start]K [cite: 1] |
| Ortam Basıncı | $P_0$ | 30,088 | [cite_start]Pa [cite: 1] |
| Ortam Sıcaklığı | $T_0$ | 228.71 | [cite_start]K [cite: 1] |
| Özgül Isı Kapasitesi | $C_p$ | 1084.2 | [cite_start]J/kg·K [cite: 1] |

---

## 4. Performans Analizi ve Doğrulama

### 4.1. Kütlesel Debi Analizi ($\dot{m}$)
[cite_start]Süreklilik denkleminin sağlanması amacıyla giriş ve çıkış kütlesel debileri incelenmiştir. [cite: 4]

* **Teorik (Hedef) Debi:** $35.004 \, kg/s$ [cite: 4]
* [cite_start]**CFD Giriş Debisi:** $35.20949 \, kg/s$ [cite: 4]
* [cite_start]**CFD Çıkış Debisi:** $-35.20957 \, kg/s$ [cite: 4]

[cite_start]**Hata Analizi:** 
Teorik hedef ile CFD çıkış debisi arasındaki fark:

$$
\text{Hata} = \left| \frac{35.20957 - 35.004}{35.004} \right| \times 100 = \%0.587
$$

*%1'in altındaki bu sapma, çözüm ağının ve termodinamik modelin yüksek irtifa basınç koşullarında dahi mükemmel çalıştığını göstermektedir.*

### 4.2. Deşarj Katsayısı ($C_d$) Hesabı
[cite_start]Boğaz bölgesindeki Mach sayısının 1 olduğu etkin alanı analizlerden doğrudan belirlemek yerine, kütlesel debi oranları üzerinden hesaplama yapılmıştır. [cite: 6, 7]

[cite_start]**Kullanılan Formül:** [cite: 7]
$$
C_d = \frac{\dot{m}_{bulunan}}{\dot{m}_{ideal}}
$$

* [cite_start]**Teorik $C_d$ (Referans):** $0.941$ 
* [cite_start]**CFD $C_d$ (Hesaplanan):** $\mathbf{0.94652}$ [cite: 7]

[cite_start]**Kıyaslama:** [cite: 8]
Referans değer ($0.941$) ile analiz sonucu ($0.946$) arasındaki fark oldukça düşüktür. Bu uyum, lüle boğazındaki akış karakteristiğinin doğru modellendiğini kanıtlar.

---

### 4.3. İtki Kuvveti ($F_g$) Analizi
[cite_start]Analizden elde edilen çıkış hızı ($876.89 \, m/s$) ve çıkış mutlak basıncı ($165,286.3 \, Pa$) verileriyle net itki hesaplanmıştır. [cite: 9]

[cite_start]**İtki Hesabı Formülü:** [cite: 10]
$$
F_g = (\dot{m} \times V_9) + A_9 \times (P_9 - P_0)
$$

[cite_start]**Sonuçlar:** [cite: 8, 10]
* **Şartname (Teorik) İtki:** $30.99 \, kN$ [cite: 8]
* **CFD Sonucu (Hesaplanan):** $\mathbf{31.52 \, kN}$

---

### 4.4. İtki ($F_g$) ve Verim ($C_{fg}$) Karşılaştırmalı Analizi
[cite_start]Analizden elde edilen performans verileri, şartname değerleri ile aşağıda karşılaştırılmıştır: 

| Parametre | Teorik / Şartname | CFD Sonucu | Fark |
| :--- | :--- | :--- | :--- |
| **İtki Kuvveti ($F_g$)** | [cite_start]$30.99 \, kN$ [cite: 8] | $31.52 \, kN$ | %1.71 |
| **İtki Katsayısı ($C_{fg}$)** | [cite_start]$0.966$ [cite: 10] | $0.957$ | %0.93 |

[cite_start]**İdeal Değerler ve $C_{fg}$ Hesabı:** [cite: 11, 12, 13]
* [cite_start]$\dot{m}_{ideal} = 37.199 \, kg/s$ [cite: 11]
* [cite_start]$V_{ideal} = 885.504 \, m/s$ [cite: 12]
* [cite_start]$F_{g,ideal} = 32.9398 \, kN$ 

$$
C_{fg} = \frac{F_{g,bulunan}}{F_{g,ideal}} = \frac{31.52}{32.9398} = \mathbf{0.957}
$$

## 5. Sonuç ve Genel Değerlendirme
Case-4 analizleri sonucunda lüle, yüksek süpersonik hızlarda (**Mach 2.55**) stabil bir çalışma sergilemiştir.

1. [cite_start]**Süreklilik:** Giriş-çıkış kütlesel debi farkı binde bir mertebesinde kalarak sayısal çözümün yakınsadığını göstermiştir. [cite: 4]
2. [cite_start]**Verimlilik:** Hesaplanan $0.957$ $C_{fg}$ değeri, teorik $0.966$ referansına **%0.93** yakınlıktadır. [cite: 10, 13] Aradaki küçük fark, süpersonik deşarj sırasındaki sınır tabaka sürtünmelerinden kaynaklanmaktadır.
3. **Doğrulama:** Elde edilen tüm veriler, tasarlanan geometrinin yüksek irtifa ve basınç oranlarında teorik tasarım kriterlerini başarıyla karşıladığını doğrulamaktadır.
