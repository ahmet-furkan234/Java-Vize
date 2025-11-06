# 🧱 **Constructor (Yapıcı Metot) Nedir?**

**Constructor**, bir sınıftan **nesne oluşturulduğunda** otomatik olarak çalışan özel metottur.

> Yani `new` ile nesne oluşturduğunda ilk çalışan şey **constructor**’dır.

---

## 🎯 Constructor’ın Özellikleri

| Özellik                                              | Açıklama                                      |
| ---------------------------------------------------- | --------------------------------------------- |
| İsmi **class ile aynı olmalı**                       | `class Ogrenci { Ogrenci() {} }`              |
| **Geri dönüş tipi yoktur**                           | `void` bile yazılmaz                          |
| Nesneyi **ilk değerlerle başlatmak için** kullanılır | Varsayılan veya özel değer atanabilir         |
| Aşırı yüklenebilir (overloading yapılabilir)         | Bir sınıfta birden fazla constructor olabilir |

---

# ✅ Örnek 1 — Parametresiz Constructor

```java
public class Ogrenci {
    String ad;
    int yas;

    // Parametresiz Constructor
    public Ogrenci() {
        System.out.println("Yeni öğrenci oluşturuldu!");
    }
}
```

### Kullanım:

```java
Ogrenci o = new Ogrenci();
```

### Çıktı:

```
Yeni öğrenci oluşturuldu!
```

---

# ✅ Örnek 2 — Parametreli Constructor

```java
public class Ogrenci {
    String ad;
    int yas;

    public Ogrenci(String ad, int yas) {
        this.ad = ad;
        this.yas = yas;
    }
}
```

### Kullanım:

```java
Ogrenci o = new Ogrenci("Ahmet", 20);
System.out.println(o.ad);
System.out.println(o.yas);
```

### Çıktı:

```
Ahmet
20
```

---

## 🔥 `this` Anahtar Kelimesi (Önemli)

Eğer parametre ile değişken adı **aynıysa**, karışmayı engeller:

```java
this.ad = ad;
```

Sol taraf → sınıfın değişkeni
Sağ taraf → parametre

---

# 🔁 Constructor Overloading (Aşırı Yükleme)

Aynı sınıfta **farklı parametrelerle** birden fazla constructor olabilir.

```java
public class Ogrenci {
    String ad;
    int yas;

    public Ogrenci() {
        System.out.println("Varsayılan öğrenci");
    }

    public Ogrenci(String ad) {
        this.ad = ad;
    }

    public Ogrenci(String ad, int yas) {
        this.ad = ad;
        this.yas = yas;
    }
}
```

---

# 🎮 Constructor İçinden Diğer Constructor’ı Çağırma (`this()`)

```java
public class Ogrenci {
    String ad;
    int yas;

    public Ogrenci() {
        this("İsimsiz", 0); // Diğer constructorı çağırıyor
    }

    public Ogrenci(String ad, int yas) {
        this.ad = ad;
        this.yas = yas;
    }
}
```

> **this()** mutlaka constructor’ın **ilk satırında** olmalıdır.

---

# 🛠️ Constructor ve Default Constructor

Eğer **hiç constructor yazmazsan** Java otomatik olarak **parametresiz** bir constructor ekler:

```java
public class Test {} // görünmez default constructor var
```

Ama **bir tane bile constructor yazarsan**, Java artık **default constructor eklemez**.

---

# 🎯 Kısa Özet

| Kural                                  | Açıklama                |
| -------------------------------------- | ----------------------- |
| Constructor ismi → Class ismiyle aynı  | Kesin kural             |
| Return type olmaz                      | `void` bile yok         |
| Overload edilebilir                    | Farklı parametrelerle   |
| `this` → Nesneye referans              | Değer karışmasını önler |
| `this()` → Diğer constructor’ı çağırır | Sadece ilk satırda      |
