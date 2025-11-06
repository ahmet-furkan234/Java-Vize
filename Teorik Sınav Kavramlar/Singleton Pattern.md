# 🧠 **Singleton Pattern Nedir?**

**Bir sınıftan uygulama boyunca yalnızca 1 tane nesne oluşturulmasını sağlar.**

Örneğin:

- Log sistemi
- Veritabanı bağlantısı
- Cache yöneticisi
- Config ayarları
- Global uygulama hizmetleri

bunların **tek tane** olması gerekir → işte **Singleton** burada devreye girer.

---

## 🎯 Özellikleri

| Özellik                                               | Açıklama                 |
| ----------------------------------------------------- | ------------------------ |
| Sadece **1 nesne** oluşur                             | Bellekte fazla örnek yok |
| **Constructor private** olur                          | Dışarıdan new yapılamaz  |
| Tek erişim noktası **static getInstance()** metodudur | Nesneyi güvenli verir    |

---

# ✅ Temel Singleton Uygulaması

```java
public class VeritabaniBaglantisi {

    private static VeritabaniBaglantisi instance;

    // 1) Constructor private → dışarıdan new engel
    private VeritabaniBaglantisi() {
        System.out.println("Veritabanı bağlantısı kuruldu.");
    }

    // 2) Nesneye erişim metodu
    public static VeritabaniBaglantisi getInstance() {
        if(instance == null) {
            instance = new VeritabaniBaglantisi();
        }
        return instance;
    }
}
```

### Kullanımı:

```java
public class Main {
    public static void main(String[] args) {
        VeritabaniBaglantisi bag1 = VeritabaniBaglantisi.getInstance();
        VeritabaniBaglantisi bag2 = VeritabaniBaglantisi.getInstance();

        System.out.println(bag1 == bag2); // true
    }
}
```

### Çıktı:

```
Veritabanı bağlantısı kuruldu.
true
```

> İki kez çağrılmasına rağmen **tek nesne oluştu** ✅

---

# 🧠 Kısa Özet

| Özellik       | Açıklama             |
| ------------- | -------------------- |
| Amaç          | Tek nesne oluşturmak |
| Constructor   | `private` olacak     |
| Nesne erişimi | `getInstance()` ile  |

---

## 🎯 Ne Zaman Kullanılmalı?

| Kullanım Durumu                         | Singleton?                    |
| --------------------------------------- | ----------------------------- |
| Tek instance olmalı (log, config, db)   | ✅ Kullan                     |
| Her istek farklı çalışma gerektiriyorsa | ❌ Kullanma                   |
| Global durum tutulacaksa                | ⚠️ Dikkat (yan etki olabilir) |
