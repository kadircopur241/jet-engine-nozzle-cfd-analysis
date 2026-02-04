# Case-5: Extended Supersonic Flow & Altitude Performance Analysis

## 1. Giriş ve Amaç
Bu rapor, jet motoru nozzle tasarımının **Case-5 (Durum 5)** koşullarındaki sayısal analiz sonuçlarını içermektedir. Bu aşamada, lülenin yüksek irtifa şartlarını temsil eden düşük ortam basıncı ($11,597 \, Pa$) altındaki performansı ve süpersonik genişleme verimi incelenmiştir.

## 2. Geometrik Parametreler
Tasarımda kullanılan lüle geometrisi, yüksek genişleme oranına göre optimize edilmiştir:

* **Giriş Alanı ($A_7$):** $0.19635 \, m^2$
* **Boğaz Alanı ($A_8$):** $0.06645 \, m^2$
* **Alan Oranı ($A_9 / A_8$):** $2.000$
* **Çıkış Alanı ($A_9$):** $0.1329 \, m^2$
* **Yakınsaklık Yarım Açısı ($\alpha$):** $30^\circ$
* **Iraksaklık Yarım Açısı ($\theta$):** $12^\circ$

## 3. Sınır Koşulları (Boundary Conditions)
Analiz, ANSYS Fluent içerisinde aşağıdaki sınır koşulları altında gerçekleştirilmiştir. Akışkan olarak İdeal Gaz (Hava) seçilmiş olup, özgül ısı kapasitesi ($C_p$) sabit $1084.2 \, J/kgK$ kabul edilmiştir.

| Parametre | Sembol | Değer | Birim |
| :--- | :--- | :--- | :--- |
| Giriş Toplam Basıncı | $P_{t7}$ | 210,000 | Pa |
| Giriş Toplam Sıcaklığı | $T_{t7}$ | 776.47 | K |
| Ortam Basıncı | $P_0$ | 11,597 | Pa |
| Ortam Sıcaklığı | $T_0$ | 216.65 | K |

---

## 4. Performans Analizi ve Doğrulama

### 4.1. Kütlesel Debi Analizi ($\dot{m}$) ve Süreklilik Kontrolü
Süreklilik denkleminin sağlanması amacıyla hem giriş-çıkış farkı hem de teorik değerle olan sapma kontrol edilmiştir.

* **Teorik (Hedef) Debi:** $18.857 \, kg/s$
* **CFD Giriş Debisi ($\dot{m}_{in}$):** $18.97863 \, kg/s$
* **CFD Çıkış Debisi ($\dot{m}_{out}$):** $-18.97797 \, kg/s$

**1. Süreklilik Hat
