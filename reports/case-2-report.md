# Case-2: Analysis & Validation Report ($M_{N0}=1.00$)

## 4. Performans Analizi ve Doğrulama

### 4.1. Kütlesel Debi Analizi ($\dot{m}$) ve Süreklilik Kontrolü

**1. Süreklilik Hatası (Giriş vs Çıkış):**
$$
\text{Hata}_{\text{süreklilik}} = \left| \frac{\dot{m}_{in} - |\dot{m}_{out}|}{\dot{m}_{in}} \right| \times 100 = \mathbf{\%0.0005}
$$

**2. Tahmin Hatası (CFD vs Teorik):**
$$
\text{Hata}_{\text{tahmin}} = \left| \frac{|\dot{m}_{out}| - 52.054}{52.054} \right| \times 100 = \mathbf{\%0.60}
$$

### 4.2. Deşarj Katsayısı ($C_d$) Karşılaştırması

$$
C_d = \frac{\dot{m}_{bulunan}}{\dot{m}_{ideal}} = \frac{52.36831}{55.316} = \mathbf{0.9467}
$$

---

### 4.3. İtki Kuvveti ($F_g$) Analizi

$$
F_g = (\dot{m} \times V_9) + A_9 \times (P_9 - P_0)
$$

**Hata Analizi:**
$$
\text{Hata} = \left| \frac{39.9615 - 40.00}{40.00} \right| \times 100 = \mathbf{\%0.096}
$$

---

### 4.4. İtki ($F_g$) ve Verim ($C_{fg}$) Karşılaştırmalı Analiz

**İdeal Değer Formülleri:**

$$
\dot{m}_{ideal} = \frac{A_8 \cdot P_{t7}}{\sqrt{T_{t7}}} \sqrt{\frac{\gamma}{R} \left( \frac{2}{\gamma+1} \right)^{\frac{\gamma+1}{\gamma-1}}}
$$

$$
V_{ideal} = \sqrt{2 \cdot C_p \cdot T_{t7} \left[ 1 - \left( \frac{P_0}{P_{t7}} \right)^{\frac{\gamma-1}{\gamma}} \right]}
$$

**İtki Katsayısı ($C_{fg}$) Hesabı:**
$$
C_{fg,CFD} = \frac{39.9615}{42.24} = \mathbf{0.946}
$$
