# **Polymorphism (Çok Biçimlilik)**

Bu konu **Inheritance + Override** yapısının gerçek gücünü gösterir.
Aynı isimli bir metodun **farklı sınıflarda farklı davranması**dır.

---

## 🎯 Polymorphism Nedir?

**Bir nesnenin**, ait olduğu sınıfa göre **farklı davranış göstermesidir.**

> Yani: **Aynı metot → farklı sonuç.**

---

## 🎭 Gerçek Hayat Örneği

“**Ses Çıkar**” komutu ortak olsun:

| Hayvan | Ses   |
| ------ | ----- |
| Kedi   | Miyav |
| Köpek  | Hav   |
| İnek   | Möö   |

**Komut aynı** → _sesCikar()_
Ama davranış **hayvana göre değişir** → _miyav / hav / möö_

İşte **Polymorphism** budur.

---

## 🧱 Kod ile Gösterelim

### Parent (Superclass)

```java
public class Hayvan {
    public void sesCikar() {
        System.out.println("Hayvan ses çıkarıyor...");
    }
}
```

### Child Sınıflar (Override ile davranış değiştiriyoruz)

```java
public class Kedi extends Hayvan {
    @Override
    public void sesCikar() {
        System.out.println("Miyav!");
    }
}
```

```java
public class Kopek extends Hayvan {
    @Override
    public void sesCikar() {
        System.out.println("Hav!");
    }
}
```

```java
public class Inek extends Hayvan {
    @Override
    public void sesCikar() {
        System.out.println("Möö!");
    }
}
```

---

### Kullanım

```java
public class Main {
    public static void main(String[] args) {
        Hayvan h1 = new Kedi();
        Hayvan h2 = new Kopek();
        Hayvan h3 = new Inek();

        h1.sesCikar();
        h2.sesCikar();
        h3.sesCikar();
    }
}
```

### Çıktı:

```
Miyav!
Hav!
Möö!
```

Aynı **sesCikar()** metodu çağrılıyor → ama sonuç **farklı**
Bu **Polymorphism**’tir ✅

---

## 🧠 Ana Mantık

```java
Hayvan h = new Kedi();  // Referans türü: Hayvan
h.sesCikar();           // Çalışan metot: Kedi’nin override metodu
```

> **Hangi metot çalışır?** > **Nesnenin türüne (new sonrası) göre.**

---

## 🔥 Method Overriding = Runtime Polymorphism

| Özellik        | Açıklama                                         |
| -------------- | ------------------------------------------------ |
| Overriding     | Metodu yeniden yazma                             |
| Çalışma Zamanı | Hangi metot çalışacağı **runtime**’da belirlenir |
| Kullanım       | Kalıtımla birlikte                               |

---

## 🧮 Method Overloading = Compile-Time Polymorphism (Ek Bilgi)

Aynı metot adı ama farklı parametreler:

```java
public void topla(int a, int b) { }
public void topla(double a, double b) { }
public void topla(int a, int b, int c) { }
```

Bu da polymorphism’tir ama **derleme zamanında** çözülür.

---

# 📝 Kısa Özet

| Tür             | Adı                       | Ne zaman belirlenir? | Örnek      |
| --------------- | ------------------------- | -------------------- | ---------- |
| **Overriding**  | Runtime Polymorphism      | Çalışma anında       | sesCikar() |
| **Overloading** | Compile-Time Polymorphism | Derleme anında       | topla()    |
