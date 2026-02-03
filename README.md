# Jet Motoru Yakınsak-Iraksak (CD) Nozzle CFD Analizi

Bu proje, bir jet motoru yarışması kapsamında gerçekleştirilen CD nozzle (lüle) akış analizlerini ve tasarım doğrulama süreçlerini içermektedir.

## Proje Hakkında
Bu çalışmanın temel amacı, yakınsak-ıraksak bir lülenin iç akış karakteristiklerini incelemek ve sayısal (CFD) sonuçları teorik hesaplamalarla doğrulamaktır.

## Teknik Detaylar
* **Yazılım:** ANSYS Fluent
* **Türbülans Modeli:** k-omega SST
* **Akışkan Modeli:** Sıkıştırılabilir hava (İdeal Gas)
* **Odak Noktaları:** Kütlesel debi doğrulaması, itki katsayısı ve Mach sayısı dağılımı.

## Proje Yapısı
Analiz dosyalarına, görsellere ve detaylı sonuç raporlarına aşağıdaki klasörlerden ulaşabilirsiniz:
* **analysis-files/:** ANSYS Fluent kurulum ve çözüm dosyaları.
* **images/:** Mach sayısı ve basınç dağılımı kontur grafikleri.
* **report/:** Analiz sonuçlarının teorik verilerle karşılaştırıldığı detaylı rapor.

## Özet

Bu çalışmada, bir jet motoru yarışması kapsamında tasarlanan yakınsak–ıraksak (CD) nozulun iç akış karakteristikleri sayısal akışkanlar dinamiği (CFD) yöntemiyle incelenmiştir. Analizler ANSYS Fluent kullanılarak gerçekleştirilmiş, sıkıştırılabilir akış varsayımı altında Mach sayısı, basınç dağılımları ve kütlesel debi değerleri elde edilmiştir. Sayısal sonuçlar, teorik akış hesaplamaları ile karşılaştırılarak nozul tasarımı doğrulanmıştır.


## Analiz Sonuçları (Case-1)

Aşağıdaki tablo, tasarımın temel akış karakteristiklerini ve sayısal analiz sonuçlarını içermektedir:

## Analiz Sonuçları (7 Farklı Durum)

Farklı basınç ve geometrik parametreler altında yapılan analizlerin görsel sonuçlarına aşağıdaki linklerden ulaşabilirsiniz:

| Analiz Durumu | Basınç Dağılımı | Mach Sayısı | Mesh Yapısı |
| :--- | :--- | :--- | :--- |
| **Durum 1 (Case-1)** | [Görüntüle](./images/case-1/case-1-pressure.png) | [Görüntüle](./images/case-1/case-1-mach.png) | [Görüntüle](./images/case-1/case-1-mesh.png) |
| **Durum 2 (Case-2)** | [Görüntüle](./images/case-2/case-2-pressure.png) | [Görüntüle](./images/case-2/case-2-mach.png) | [Görüntüle](./images/case-2/case-2-mesh.png) |
| **Durum 3 (Case-3)** | [Görüntüle](./images/case-3/case-3-pressure.png) | [Görüntüle](./images/case-3/case-3-mach.png) | [Görüntüle](./images/case-3/case-3-mesh.png) |
| ... | ... | ... | ... |

---

**Hazırlayan:** Abdülkadir Çopuroğlu

**İletişim:** [kadircopuroglu241@gmail.com](mailto:kadircopuroglu241@gmail.com)

**Okul:** İstanbul Teknik Üniversitesi - Makina Mühendisliği
