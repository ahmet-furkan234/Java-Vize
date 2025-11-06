## 🧱 1) Class Nedir?

**Class**, nesneleri üretmek için kullanılan bir **şablondur / taslaktır**.
Class içinde **özellikler** (değişkenler) ve **davranışlar** (metotlar) bulunur.

---

## 🧩 Class Yapısı (Genel Şablon)

```java
public class ClassAdi {
    // 1. Özellikler (Fields)
    // 2. Constructor (İsteğe bağlı)
    // 3. Davranışlar (Methods)
}
```

---

## 👤 Örnek: Öğrenci Sınıfı

```java
public class Ogrenci {

    // 1. Özellikler
    int ogrNo;
    String ad;
    String sinif;

    // 2. Davranış (Metot)
    public void bilgileriYazdir() {
        System.out.println("Öğrenci No: " + ogrNo);
        System.out.println("Ad: " + ad);
        System.out.println("Sınıf: " + sinif);
    }
}
```

---

## 🏗️ Nesne Üretme (Object Oluşturma)

```java
public class Main {
    public static void main(String[] args) {

        Ogrenci ogr1 = new Ogrenci(); // Nesne oluştur
        ogr1.ogrNo = 1;
        ogr1.ad = "Ahmet";
        ogr1.sinif = "10/A";

        ogr1.bilgileriYazdir();
    }
}
```

### Çıktı

```
Öğrenci No: 1
Ad: Ahmet
Sınıf: 10/A
```

---

## 🛠️ 2) Constructor (Yapıcı Metot)

- Nesne **oluşturulurken** çalışan metottur.
- İsmi **class ile aynı olur**.
- **Geri dönüş tipi olmaz** (void bile yazılmaz).

### Parametresiz Constructor

```java
public Ogrenci() {
    System.out.println("Yeni öğrenci oluşturuldu!");
}
```

### Parametreli Constructor

```java
public Ogrenci(int ogrNo, String ad, String sinif) {
    this.ogrNo = ogrNo;
    this.ad = ad;
    this.sinif = sinif;
}
```

### Kullanımı:

```java
Ogrenci ogr2 = new Ogrenci(2, "Mehmet", "11/B");
ogr2.bilgileriYazdir();
```

---

## 🎯 `this` Anahtar Kelimesi

`this`, **o anki nesneyi** ifade eder.

```java
this.ad = ad;
```

Eğer parametrenin adı ve değişkenin adı aynıysa **karışmayı önler.**

---

## 🔒 3) Access Modifiers (Erişim Belirleyiciler)

| Belirleyici | Erişim                              | Kullanım                        |
| ----------- | ----------------------------------- | ------------------------------- |
| `public`    | Her yerden erişilir                 | Genel kullanım                  |
| `private`   | Sadece class içinden                | Encapsulation’da çok kullanılır |
| `protected` | Aynı paket + kalıtım alan class’lar | Mirasta kullanılır              |
| (default)   | Sadece aynı paket                   | Paket içi kullanım              |

### Örnek:

```java
public class Ogrenci {
    private int ogrNo;
    private String ad;
}
```

Bu durumda `ogrNo` **dışarıdan direkt değiştirilemez**.
