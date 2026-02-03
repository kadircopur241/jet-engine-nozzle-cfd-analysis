
# Case-1: Design Point (DP) Analysis & Validation Report

## 1. Giriş ve Amaç
Bu rapor, tasarlanan Yakınsak-Iraksak (CD) lülenin **Design Point (DP)** koşullarındaki aerodinamik performansını doğrulamak amacıyla hazırlanmıştır. Analiz sonuçları (CFD), teorik termodinamik hesaplamalar ve tasarım şartnamesi verileri ile karşılaştırılarak sayısal modelin doğruluğu test edilmiştir.

## 2. Geometrik Parametreler
Lüle tasarımında akış ayrılmalarını önlemek ve optimum genişlemeyi sağlamak amacıyla aşağıdaki geometrik kabuller yapılmıştır:

* **Giriş Alanı ($A_7$):** $0.19632 \, m^2$
* **Boğaz Alanı ($A_8$):** $0.06675 \, m^2$
* **Alan Oranı ($A_9/A_8$):** $1.178$
* **Yakınsaklık Yarım Açısı ($\alpha$):** $30^\circ$
* **Iraksaklık Yarım Açısı ($\theta$):** $12^\circ$

## 3. Sınır Koşulları (Boundary Conditions)
Analiz, ANSYS Fluent içerisinde aşağıdaki işletme koşulları altında gerçekleştirilmiştir. Akışkan olarak **İdeal Gaz** (Hava) seçilmiş olup, vizkozite için **Sutherland** modeli, ısı kapasitesi ($C_p$) için ise sıcaklığa bağlı polinom kullanılmıştır ($C_p \approx 1084.2 \, J/kgK$).

| Parametre | Sembol | Değer | Birim |
| :--- | :--- | :--- | :--- |
| Giriş Toplam Basıncı | $P_{t7}$ | 420,000 | Pa |
| Giriş Toplam Sıcaklığı | $T_{t7}$ | 800 | K |
| Ortam Basıncı | $P_0$ | 101,325 | Pa |
| Ortam Sıcaklığı | $T_0$ | 288.15 | K |

---

## 4. Performans Analizi ve Doğrulama

### 4.1. Kütlesel Debi Analizi ($\dot{m}$)
Süreklilik denkleminin sağlanması ve kütle korunumunun kontrolü amacıyla giriş ve çıkış debileri incelenmiştir.

* **Teorik (Hedef) Debi:** $37.714 \, kg/s$
* **CFD Giriş Debisi:** $38.014 \, kg/s$
* **CFD Çıkış Debisi:** $-38.012 \, kg/s$ (Net akış)

**Hata Analizi:**
Teorik hedef ile CFD sonucu arasındaki fark:
$$\text{Hata} = \left| \frac{38.012 - 37.714}{37.714} \right| \times 100 = \%0.79$$
*%1'in altındaki bu sapma, çözüm ağının ve sınır koşullarının yüksek doğruluğunu göstermektedir.*

### 4.2. Deşarj Katsayısı ($C_d$) Hesabı
Sıkıştırılabilir akışlarda boğaz bölgesindeki efektif alanı belirlemek zor olduğu için, $C_d$ hesabı kütlesel debiler üzerinden yapılmıştır.

Kullanılan Formül:
$$C_d = \frac{\dot{m}_{bulunan}}{\dot{m}_{ideal}}$$

Termodinamik denklemlerle hesaplanan **İdeal (Isentropic) Kütlesel Debi ($\dot{m}_{ideal}$)** değeri **$40.07 \, kg/s$** olarak bulunmuştur.

* **Teorik $C_d$ (Referans):** $0.941$
* **CFD $C_d$ (Hesaplanan):** $38.012 / 40.07 = 0.9485$

**Karşılaştırma:**
Referans değer ile analiz sonucu arasındaki fark **%0.8** mertebesindedir. Bu sonuç, viskoz etkilerin ve sınır tabaka oluşumunun analizde doğru modellendiğini kanıtlar.

---

### 4.3. İtki Kuvveti ($F_g$) Analizi
Analiz sonucunda lüle çıkış düzleminden (Station 9) alınan ortalama veriler şöyledir:
* **Çıkış Hızı ($V_9$):** $686.264 \, m/s$
* **Çıkış Basıncı ($P_9$):** $119,938.5 \, Pa$
* **Çıkış Alanı ($A_9$):** $0.0786 \, m^2$ (Alan oranından hesaplanmıştır)

İtki Hesabı Formülü:
$$F_g = (\dot{m} \times V_9) + A_9 \times (P_9 - P_0)$$

Hesaplama:
$$F_{g,CFD} = (38.012 \times 686.264) + 0.0786 \times (119938.5 - 101325)$$
$$F_{g,CFD} \approx 26,086 + 1,463 = 27,549 \, N \approx \mathbf{27.55 \, kN}$$

**Doğrulama:**
* **Şartname (Teorik) İtki:** $26.98 \, kN$
* **CFD Sonucu:** $27.55 \, kN$
* **Sapma:** ~%2.1 (Kabul edilebilir sınırlar içerisindedir).

---

### 4.4. İtki Katsayısı ($C_{fg}$) ve Verim
Nozzle performansının en önemli göstergesi olan itki katsayısı, CFD itkisinin ideal itkiye oranıyla bulunmuştur.

İdeal çıkış hızı ($V_{ideal}$), izentropik genişleme varsayımıyla **$710.193 \, m/s$** olarak hesaplanmıştır.
$$F_{g,ideal} = \dot{m}_{ideal} \times V_{ideal} = 40.07 \times 710.193 \approx \mathbf{28.46 \, kN}$$

İtki Katsayısı Hesabı:
$$C_{fg} = \frac{F_{g,bulunan}}{F_{g,ideal}} = \frac{27.55}{28.46} = \mathbf{0.968}$$

* **Teorik $C_{fg}$:** $0.970$
* **Hesaplanan $C_{fg}$:** $0.968$
* **Sonuç:** %0.2'lik mükemmel bir uyum yakalanmıştır.

## 5. Sonuç
Design Point (DP) koşullarında yapılan CFD analizi, teorik tasarım verileriyle yüksek tutarlılık göstermiştir.
1. Kütlesel debi hatası **%0.79**,
2. Deşarj katsayısı ($C_d$) hatası **%0.8**,
3. İtki katsayısı ($C_{fg}$) hatası **%0.2** seviyesindedir.

Bu sonuçlar, tasarlanan lülenin ve oluşturulan sayısal modelin (Mesh + Setup) güvenilir olduğunu kanıtlamaktadır.
