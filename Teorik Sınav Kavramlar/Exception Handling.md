# ⚠️ **Exception Handling Nedir?**

Program çalışırken **beklenmeyen durumlar** oluşabilir:

- Dosya bulunamadı
- Null değerle işlem yapıldı
- Bölme işlemi sıfıra yapıldı
- Sunucuya bağlanılamadı

Bu tip durumlara **Exception (İstisna)** denir.

> **Exception Handling**, bu hataları **kontrollü şekilde yönetme işlemidir.**
> Program **çökmek yerine**, hatayı **yakalar** ve **alternatif tepki** verir.

---

## 🎭 Java'da Hata Yakalama Yapısı

```java
try {
    // Hata fırlatma ihtimali olan kodlar
} catch (ExceptionTürü e) {
    // Hata olduğunda çalışacak kodlar
} finally {
    // Hata olsa da olmasa da çalışır (opsiyonel)
}
```

---

# 🧨 Örnek: Sıfıra Bölme Hatası

```java
public class Main {
    public static void main(String[] args) {
        try {
            int a = 10 / 0; // ArithmeticException
        } catch (ArithmeticException e) {
            System.out.println("Sıfıra bölme hatası: " + e.getMessage());
        }
    }
}
```

### Çıktı:

```
Sıfıra bölme hatası: / by zero
```

---

# 🔍 Çoklu `catch` Kullanımı

```java
try {
    String s = null;
    s.length(); // NullPointerException
} catch (NullPointerException e) {
    System.out.println("Null referans hatası!");
} catch (Exception e) {
    System.out.println("Genel hata!");
}
```

> En **özel hata** üstte, **genel** olan en altta olmalı ✅

---

# ✅ `finally` Bloğu

**Hata olsa da olmasa da** çalışır.
Özellikle **dosya, veritabanı bağlantısı kapatma** gibi durumlarda kullanılır.

```java
try {
    System.out.println("İşlem yapılıyor...");
} catch (Exception e) {
    System.out.println("Hata oluştu.");
} finally {
    System.out.println("Kaynaklar kapatıldı.");
}
```

---

# 🌟 `throw` ve `throws` Farkı

| Kelime   | Görev                                        |
| -------- | -------------------------------------------- |
| `throw`  | Elle exception fırlatır                      |
| `throws` | Metodun exception fırlatabileceğini belirtir |

### `throw` Örneği

```java
public void yasKontrol(int yas) {
    if (yas < 18) {
        throw new IllegalArgumentException("Yaş 18'den küçük olamaz!");
    }
}
```

### `throws` Örneği

```java
public void dosyaOku() throws IOException {
    // dosya işlemleri
}
```

---

# 🧱 Checked ve Unchecked Exception

| Tür           | Açıklama                         | Örnek                                     | Zorunlu try-catch |
| ------------- | -------------------------------- | ----------------------------------------- | ----------------- |
| **Checked**   | Derleme zamanında kontrol edilir | IOException, SQLException                 | ✅ Evet           |
| **Unchecked** | Çalışma zamanında oluşur         | NullPointerException, ArithmeticException | ❌ Hayır          |

---

# 🧠 En Çok Karşılaşılan Exception'lar

| Hata                             | Açıklama                         |
| -------------------------------- | -------------------------------- |
| `NullPointerException`           | Null referans ile işlem yapılmış |
| `ArithmeticException`            | Sıfıra bölme                     |
| `ArrayIndexOutOfBoundsException` | Dizide olmayan index             |
| `IOException`                    | Dosya işlemi hatası              |
| `SQLException`                   | Veritabanı hatası                |

---

# 🏁 Mini Uygulama (Gerçekçi Örnek)

```java
public class HesapMakinesi {

    public int bol(int a, int b) {
        if (b == 0) {
            throw new ArithmeticException("Bölünen sayı sıfır olamaz!");
        }
        return a / b;
    }
}

public class Main {
    public static void main(String[] args) {
        try {
            HesapMakinesi h = new HesapMakinesi();
            System.out.println(h.bol(10, 0));
        } catch (ArithmeticException e) {
            System.out.println("Hata: " + e.getMessage());
        }
    }
}
```

---

# 🎯 Kısa Özet

| Yapı    | Görev                                   |
| ------- | --------------------------------------- |
| try     | Riskli kod bloğu                        |
| catch   | Hata yakalama                           |
| finally | Her durumda çalışır                     |
| throw   | Exception fırlatır                      |
| throws  | Metodun hata fırlatabileceğini bildirir |
