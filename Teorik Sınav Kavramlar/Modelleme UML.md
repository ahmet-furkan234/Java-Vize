# 🧩 **UML (Unified Modeling Language) Nedir?**

**UML**, bir sistemi analiz etmek ve tasarlamak için kullanılan **standart modelleme dilidir.**
Yani yazılımın **nasıl çalışacağını, hangi parçaları içereceğini ve bu parçaların birbirleriyle nasıl iletişim kuracağını** gösterir.

> Kod yazmaya başlamadan önce **mimariyi planlamak** için kullanılır.

---

# 🎯 UML Neden Kullanılır?

| Amaç                 | Açıklama                                          |
| -------------------- | ------------------------------------------------- |
| İletişim             | Ekip içinde herkesin aynı şeyi anlamasını sağlar  |
| Planlama             | Yazılımdaki parçaları önceden belirler            |
| Dökümantasyon        | Projenin mimarisi anlaşılır hale gelir            |
| Hataları erken bulma | Kod yazmadan önce tasarım hatalarını fark edersin |

---

# 📌 UML’de Yaygın Kullanılan Diyagramlar

| Diagram              | Ne Gösterir?                | Ne Zaman Kullanılır?                 |
| -------------------- | --------------------------- | ------------------------------------ |
| **Use Case Diagram** | Kullanıcı → Sistem ilişkisi | Projenin _ne yaptığını_ anlamak için |
| **Class Diagram**    | Sınıflar ve ilişkiler       | Kod tasarımında (en kritik diagram)  |
| **Sequence Diagram** | Nesnelerin mesajlaşması     | İş akışını göstermek için            |
| **Activity Diagram** | İş süreçleri ve akışlar     | Mantık akışlarını açıklamak için     |
| **State Diagram**    | Nesnenin durum değişimleri  | Duruma göre çalışan sistemlerde      |

Şimdi en önemlisi olan **Class Diagram** ile başlıyoruz.

---

# 🧱 **Class Diagram (Sınıf Diyagramı)**

**Sınıfları, özelliklerini (fields), metotlarını ve diğer sınıflarla ilişkilerini gösterir.**

### Class Yapısı:

```
+---------------------+
|    Sınıf Adı        |
+---------------------+
| Özellikler (Fields) |
+---------------------+
| Davranışlar (Methods) |
+---------------------+
```

---

## 🎓 Örnek: Öğrenci Sistemi

### Sınıflar:

- Ogrenci
- Ogretmen
- Ders

### Class Diagram:

```
+-------------------+
|     Ogrenci       |
+-------------------+
| - ogrNo: int      |
| - ad: String      |
+-------------------+
| + dersAl(Ders)    |
+-------------------+

+-------------------+
|    Ogretmen       |
+-------------------+
| - ad: String      |
| - brans: String   |
+-------------------+
| + dersVer(Ders)   |
+-------------------+

+-------------------+
|      Ders         |
+-------------------+
| - dersAdi: String |
+-------------------+
| + baslat()        |
+-------------------+
```

---

# 🔗 UML İlişki Türleri

| Tür             | Sembol | Açıklama                            | Örnek               |
| --------------- | ------ | ----------------------------------- | ------------------- |
| **Association** | →      | İlişkili ama bağımlı değil          | Öğrenci → Ders alır |
| **Aggregation** | ○→     | “Has-a” ama nesne bağımsızdır       | Okul ○→ Öğrenci     |
| **Composition** | ◆→     | “Has-a” ama nesne bağımsız değildir | Araba ◆→ Motor      |
| **Inheritance** | △→     | “is-a” (extends)                    | Kedi △→ Hayvan      |

---

### ÖRNEK: Composition

```
Araba ◆→ Motor
```

Araba yok → Motorun anlamı yok → **Bileşim**

---

### ÖRNEK: Inheritance

```
Hayvan △→ Kedi
```

Kedi **bir** hayvandır → **Kalıtım**

---

## 🧠 Şimdi Küçük Bir Uygulama

Aşağıdaki modeli UML’e dökeceğiz:

```
Kullanıcı
  - isim
  - email
  - girişYap()

Admin (Kullanıcı'dan türetilir)
  - sistemKontrol()

Sipariş
  - ürün
  - toplamTutar
```

### UML Class Diagram:

```
            △
        +---------+
        | Kullanici|
        +----------+
        | isim     |
        | email    |
        +----------+
        | girisYap()|
        +----------+
              |
              |
        +-----------+
        |   Admin   |
        +-----------+
        | sistemKontrol() |
        +-----------+

+------------------+
|    Siparis       |
+------------------+
| ürün: String     |
| toplamTutar: Double |
+------------------+
| siparisVer()     |
+------------------+
```
