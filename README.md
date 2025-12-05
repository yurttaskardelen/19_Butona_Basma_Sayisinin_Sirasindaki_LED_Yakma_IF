# 19_Butona_Basma_Sayisinin_Sirasindaki_LED_Yakma_IF (Sequential Control)

Bu proje, **STM32F407-Discovery** kartı üzerinde butona her basıldığında sıradaki bir sonraki LED'i yakan bir uygulamadır.

Bu depo, bir sayaç değişkeni (`basma_sayisi`) ve `if` blokları kullanılarak donanım çıkışlarının nasıl sırayla kontrol edilebileceğini gösterir.


---

### 🎯 Proje Senaryosu

Sistem, `basma_sayisi` değişkenini takip eder ve her basışta farklı bir pini aktif eder. Ayrıca butona basılı tutulduğu sürece ilgili LED yanık kalır.

1.  **1. Basış:** `PA1` üzerindeki LED yanar. Buton bırakılınca söner.
2.  **2. Basış:** `PA2` üzerindeki LED yanar. Buton bırakılınca söner.
3.  **3. Basış:** `PA3` üzerindeki LED yanar. Buton bırakılınca söner.
4.  **4. Basış:** `PA4` üzerindeki LED yanar. Buton bırakılınca söner ve sayaç sıfırlanır.
5.  **Sonraki Basış:** Döngü tekrar `PA1`'den başlar.

---

### ⚙️ Pull-Up Konfigürasyonu

Projenin düzgün çalışması için `.ioc` dosyasında buton pininin (`PA0`) **Pull-Up** olarak ayarlanması gereklidir.

* **Pin:** `PA0` -> `GPIO_Input`
* **Resistor:** `Pull-up`

<img width="843" height="644" alt="image" src="https://github.com/user-attachments/assets/a5bccc60-b813-4f18-9e9a-a4f0fd3519bf" />

---

### 🛠️ Gerekli Donanım

* **1x** STM32F407-Discovery Geliştirme Kartı
* **4x** LED (Sıralı efekt için tercihen yan yana dizilmiş)
* **4x** 220 Ohm Direnç
* **1x** Push-Button
* **Breadboard ve Jumper Kablolar**

---

### 🔌 Devre Şeması

Buton bağlantısı **Pull-Up** mantığına göre (GND'ye) yapılmalıdır.

| Bileşen | STM32 Pini | Bağlantı Detayı |
| :--- | :--- | :--- |
| **Buton** | `PA0` | Bir bacak **PA0**, diğer bacak **GND** |
| **LED 1** | `PA1` | Anot -> **PA1**, Katot -> Direnç -> **GND** |
| **LED 2** | `PA2` | Anot -> **PA2**, Katot -> Direnç -> **GND** |
| **LED 3** | `PA3` | Anot -> **PA3**, Katot -> Direnç -> **GND** |
| **LED 4** | `PA4` | Anot -> **PA4**, Katot -> Direnç -> **GND** |


<img width="489" height="417" alt="image" src="https://github.com/user-attachments/assets/7f89e4d2-4b29-4f6d-9428-3d9d0439f4b2" />

---

### 💻 Kod Bloğu

<img width="523" height="890" alt="image" src="https://github.com/user-attachments/assets/b79514e4-4543-4118-8f47-d2c718cddb92" />

---

### 🚀 Nasıl Kullanılır?

1.  Bu depoyu klonlayın (`git clone ...`).
2.  STM32CubeIDE yazılımını açın.
3.  `File > Open Projects from File System...` seçeneği ile proje klasörünü seçin.
4.  Proje içindeki `.ioc` dosyasını açarak pin yapılandırmasını inceleyebilirsiniz.
5.  Derleyin (Build) ve ST-Link V2 üzerinden kartınıza yükleyin (Run).
