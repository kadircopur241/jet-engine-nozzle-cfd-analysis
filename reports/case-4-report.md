# Case-5: Süpersonik Lüle CFD Analizi ve Performans Doğrulaması

Bu proje, yüksek irtifa koşullarında (Case-5) çalışan süpersonik bir lülenin (nozzle) ANSYS Fluent kullanılarak gerçekleştirilen hesaplamalı akışkanlar dinamiği (CFD) analizlerini ve teorik doğrulamalarını içerir.

## 📋 Proje Özeti
Bu çalışmanın amacı, belirlenen sınır koşulları altında lülenin kütlesel debi tutarlılığını, şok dalgası oluşumlarını ve itki performansını incelemektir. Analiz sonuçları, izentropik akış denklemleri ve teorik hedeflerle karşılaştırılarak doğrulama yapılmıştır.

## ⚙️ Geometri ve Mesh Yapısı

Analiz edilen lüle, yakınsak-ıraksak (De Laval) geometriye sahiptir. Akış gradyanlarını doğru yakalamak için yapısal (structured) bir çözüm ağı kullanılmıştır.

* [cite_start]**Giriş Alanı ($A_7$):** $0.19635 \, m^2$ [cite: 1]
* [cite_start]**Boğaz Alanı ($A_8$):** $0.06645 \, m^2$ [cite: 1]
* [cite_start]**Alan Oranı ($A_9/A_8$):** $2.000$ [cite: 1]
* [cite_start]**Yakınsaklık/Iraksaklık Açısı:** $30^\circ$ / $12^\circ$ [cite: 3]

![Mesh Kalitesi](case-5-mesh.png)
*Şekil 1: Mesh Ortogonal Kalite Dağılımı*

## 🧪 Sınır Koşulları (Boundary Conditions)

[cite_start]Analizler, ANSYS Fluent içerisinde parametrik olarak aşağıdaki koşullarda gerçekleştirilmiştir[cite: 2]:

| Parametre | Değer | Birim |
| :--- | :--- | :--- |
| **Giriş Basıncı ($P_{in}$)** | 210,000 | [cite_start]Pa [cite: 1] |
| **Giriş Sıcaklığı ($T_{in}$)** | 776.47 | [cite_start]K [cite: 1] |
| **Ortam Basıncı ($P_{amb}$)** | 11,597 | [cite_start]Pa [cite: 1] |
| **Ortam Sıcaklığı ($T_{amb}$)** | 216.65 | [cite_start]K [cite: 1] |
| **Özgül Isı ($C_p$)** | 1084.2 | [cite_start]J/kgK [cite: 1] |

## 📊 Analiz Sonuçları ve Doğrulama

### 1. Kütlesel Debi ve Deşarj Katsayısı ($C_d$)

Süreklilik denkleminin sağlanması ve kütle korunumunun kontrolü:

* [cite_start]**Teorik Kütlesel Debi:** $18.857 \, kg/s$ [cite: 4]
* [cite_start]**CFD Giriş Debisi:** $18.97863 \, kg/s$ [cite: 4]
* [cite_start]**CFD Çıkış Debisi:** $-18.97797 \, kg/s$ [cite: 4]

**Deşarj Katsayısı Hesabı:**
[cite_start]Mach sayısının 1 olduğu sonlu element bölgesini belirleme zorluğu nedeniyle, $C_d$ hesabı kütlesel debi oranları üzerinden yapılmıştır[cite: 6, 7]:

$$
C_d = \frac{\dot{m}_{bulunan}}{\dot{m}_{ideal}} = \frac{18.978}{20.038} = \mathbf{0.956}
$$

* *Teorik $C_d$:* 0.940
* [cite_start]*Hesaplanan $C_d$:* 0.956 [cite: 7]

### 2. Akış Görselleştirmesi

Lüle içerisindeki Mach sayısı dağılımı, akışın boğazda ses hızına ulaştığını ve çıkışta süpersonik hızlara (M > 2.5) çıktığını göstermektedir.

![Mach Sayısı](case-5-mach-number.png)
*Şekil 2: Mach Sayısı Konturu*

![Basınç Dağılımı](case-5-pressure.png)
*Şekil 3: Statik Basınç Dağılımı*

### 3. İtki Kuvveti ($F_g$) ve Performans

[cite_start]Lüle performansının en önemli göstergesi olan itki kuvveti aşağıdaki formül ile hesaplanmıştır[cite: 10]:

$$F_g = (\dot{m} \cdot V_{çıkış}) + A_{çıkış}(P_{çıkış} - P_{ortam})$$

[cite_start]**Analiz Verileri[cite: 9]:**
* $V_{çıkış}$: $876.89 \, m/s$
* $P_{çıkış}$: $20,213.8 \, Pa$

**Sonuçlar:**
* **Hesaplanan İtki ($F_{g, CFD}$):** $17.786 \, kN$
* [cite_start]**İdeal İtki ($F_{g, ideal}$):** $18.318 \, kN$ [cite: 13]

### 4. İtki Verimi ($C_{fg}$)

$$C_{fg} = \frac{F_{g, CFD}}{F_{g, ideal}}$$

* **Teorik Hedef $C_{fg}$:** 0.961
* [cite_start]**Analiz Sonucu $C_{fg}$:** **0.971** [cite: 13]

## 📝 Sonuç

Yapılan CFD analizleri sonucunda, Case-5 koşulları için tasarlanan lülenin:
1.  Kütle korunumunu %0.1 hata payı ile sağladığı,
2.  İdeal itki değerine %97 oranında yaklaştığı ($C_{fg} = 0.971$),
3.  Teorik deşarj katsayısı ile uyumlu çalıştığı doğrulanmıştır.

---
*Bu çalışma ANSYS Fluent 2023 R1 kullanılarak gerçekleştirilmiştir.*
