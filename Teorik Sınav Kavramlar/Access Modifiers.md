# 🔐 **Access Modifiers (Erişim Belirleyiciler)**

Java’da bir **sınıf, metot veya değişkenin nereden erişilebileceğini** belirleyen anahtar kelimelerdir.

| Access Modifier          | Erişim Alanı                     | Nereden Görülür?                |
| ------------------------ | -------------------------------- | ------------------------------- |
| **public**               | Her yerden                       | Tüm paketler, projeler          |
| **protected**            | Aynı paket + miras alan sınıflar | Inheritance olduğunda önemlidir |
| **default** _(yazılmaz)_ | Sadece aynı paket                | Paket dışından görünmez         |
| **private**              | Sadece aynı sınıf                | En kısıtlı erişim               |

---

## 1) **public**

- En geniş erişim.
- Her yerden kullanılabilir.

```java
public class Araba {
    public String marka;
}
```

Kullanım:

```java
Araba a = new Araba();
a.marka = "BMW"; // Her yerden erişilir
```

---

## 2) **private**

- En kısıtlı erişim.
- Sadece aynı **class** içinde geçerlidir.
- `Encapsulation`’ın temelidir.

```java
public class Araba {
    private String model;

    public String getModel() {
        return model;
    }

    public void setModel(String model) {
        this.model = model;
    }
}
```

> Dışarıdan **get/set** ile kontrol ederek erişilir.

---

## 3) **default** (Belirtilmezse uygulanır)

```java
class Araba { // public yazmadığımız için default
    String renk; // renk de default
}
```

- Sadece **aynı paket içinden** erişilir.
- Paket dışına çıkınca görünmez.

```java
// Paket 1
class A { int x = 10; }

// Paket 2
class B {
    A a = new A(); // ❌ Görünmez, hata verir
}
```

---

## 4) **protected**

- **Aynı paket içerisinde → public gibi**
- Ama paket dışından sadece **kalıtım (extends)** ile erişilebilir.

```java
public class Hayvan {
    protected String isim;
}
```

```java
public class Kedi extends Hayvan {
    public void yaz() {
        System.out.println(isim); // ✅ protected → miras sayesinde erişilir
    }
}
```

Ama paket dışından kalıtım yoksa:

```java
Hayvan h = new Hayvan();
h.isim; // ❌ görünmez
```

---

# 🔥 Karşılaştırma Tablosu

| Modifier      | Aynı Sınıf | Aynı Paket | Miras Alan Sınıf | Dışarıdan |
| ------------- | :--------: | :--------: | :--------------: | :-------: |
| **public**    |     ✅     |     ✅     |        ✅        |    ✅     |
| **protected** |     ✅     |     ✅     |        ✅        |    ❌     |
| **default**   |     ✅     |     ✅     |        ❌        |    ❌     |
| **private**   |     ✅     |     ❌     |        ❌        |    ❌     |

---

# 🎯 Nerede Hangisini Kullanmalıyız?

| Durum                           | Önerilen                    |
| ------------------------------- | --------------------------- |
| Nesne verileri (fields)         | **private** + getter/setter |
| Utility (yardımcı) metotlar     | **private**                 |
| Paylaşılan API metotları        | **public**                  |
| Kalıtım için ortak özellikler   | **protected**               |
| Paket içi kullanılacak sınıflar | **default**                 |

---

# 🧠 Kısacık Ezber Cümlesi

> **En dar → private → default → protected → public → En geniş**

---
