# 🔹 **this** Anahtar Kelimesi Nedir?

`this`, **bulunulan nesneyi** (o anda çalışan objeyi) ifade eder.

Yani:

> **this → Bu sınıftan oluşturulmuş olan _NESNE_**

---

## 🎯 `this` Nerede Kullanılır?

| Kullanım                                                     | Açıklama                     |
| ------------------------------------------------------------ | ---------------------------- |
| 1) Sınıf içindeki **değişkenlere** erişmek için              | Değişken adı karışmasın diye |
| 2) Aynı sınıftaki **metotları çağırmak için**                | `this.metotAdi()`            |
| 3) Bir constructor’dan **diğer constructor’ı çağırmak için** | `this()`                     |

---

# 🧱 1) **this** → Değişkenleri Belirginleştirmek İçin

Aynı isimli parametre ve sınıf değişkeni varsa **karışmayı önler.**

```java
public class Ogrenci {
    String ad;
    int yas;

    public Ogrenci(String ad, int yas) {
        this.ad = ad;   // this.ad → sınıf değişkeni
        this.yas = yas; // ad, yas → parametre
    }
}
```

Eğer `this` kullanmazsan _parametre sınıf değişkenini ezer_.

---

# 🧱 2) Sınıf İçindeki Metotları Çağırmak

```java
public class Araba {
    public void calis() {
        System.out.println("Araba çalıştı");
    }

    public void baslat() {
        this.calis(); // Aynı sınıftaki metodu çağırır
    }
}
```

`this.calis()` → `calis()` ile aynı
ama **okunabilirlik için** tercih edilir.

---

# 🧱 3) Constructor İçinden Diğer Constructor’ı Çağırma → `this()`

> `this()` **sadece constructor içinde** ve **ilk satırda** kullanılabilir.

```java
public class Kitap {
    String ad;
    double fiyat;

    public Kitap() {
        this("Bilinmeyen", 0); // Diğer constructor çağrılıyor
    }

    public Kitap(String ad, double fiyat) {
        this.ad = ad;
        this.fiyat = fiyat;
    }
}
```

---

# 🔥 Çok Önemli: `this` vs `super`

| Özellik             | this                          | super                                |
| ------------------- | ----------------------------- | ------------------------------------ |
| İşaret ettiği yer   | **Bu sınıf (current object)** | **Parent (üst sınıf)**               |
| Kullanıldığı yer    | Değişken, metot, constructor  | Üst sınıf değişken/metot/constructor |
| Constructor çağırma | `this()` → Aynı sınıf         | `super()` → Parent sınıf             |

---

# 🧠 Örnekle Özet

```java
public class Hayvan {
    String isim;

    public Hayvan(String isim) {
        this.isim = isim;
    }
}
```

```java
public class Kedi extends Hayvan {

    String renk;

    public Kedi(String isim, String renk) {
        super(isim);   // Parent constructor → Hayvan
        this.renk = renk; // Bu nesnenin değişkeni
    }
}
```

---

# 🎯 Kısa ve Öz Özet

| `this` Ne Yapar?                           | Hatırlatma      |
| ------------------------------------------ | --------------- |
| Nesnenin kendisini ifade eder              | “Bu nesne”      |
| Sınıf içi değişkenleri netleştirir         | `this.ad = ad;` |
| Aynı sınıftaki başka constructor’ı çağırır | `this()`        |
| Metot çağrısı için kullanılabilir          | `this.metot()`  |
