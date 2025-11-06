# 🧬 **Inheritance (Kalıtım) Nedir?**

**Bir sınıfın (Child / Subclass), başka bir sınıftan (Parent / Superclass) özellik ve metotları miras almasıdır.**

- Kod tekrarını azaltır.
- Ortak özellikleri yukarı (parent) sınıfta toplar.
- Daha düzenli ve yönetilebilir bir yapı sağlar.

---

## 🏛 Örnek Durum (Gerçek Hayat)

**Hayvan** → Geneldir
**Kedi, Köpek** → Hayvan’dan türetilebilir.

| Hayvan (Parent) | Kedi (Child) | Köpek (Child) |
| --------------- | ------------ | ------------- |
| isim            | tüy döker    | havlar        |
| yaş             | miyav()      | havla()       |
| yemekYer()      |              |               |

---

## 🧱 Temel Kullanım

Java'da kalıtım `extends` ile yapılır:

```java
class ChildClass extends ParentClass {
}
```

---

## 🐾 Örnek Kod

### Parent Sınıf (Superclass)

```java
public class Hayvan {
    String isim;
    int yas;

    public void yemekYer() {
        System.out.println(isim + " yemek yiyor...");
    }
}
```

### Child Sınıf (Subclass)

```java
public class Kedi extends Hayvan {
    public void miyavla() {
        System.out.println(isim + " miyavlıyor!");
    }
}
```

### Kullanım

```java
public class Main {
    public static void main(String[] args) {

        Kedi kedi = new Kedi();
        kedi.isim = "Pamuk";
        kedi.yas = 3;

        kedi.yemekYer();  // Parent'tan geldi
        kedi.miyavla();   // Kedi'ye özel davranış
    }
}
```

### Çıktı:

```
Pamuk yemek yiyor...
Pamuk miyavlıyor!
```

---

## 🎯 Dikkat: “extends” Tekli Kalıtım

Java **tekli kalıtımı destekler**:

```java
class A {}
class B extends A {}   // ✅
class C extends B {}   // ✅ Zincir olabilir
```

Ama:

```java
class C extends A, B {} // ❌ Java’da mümkün değil
```

Çünkü **çoklu kalıtım karmaşık miras yapısı ve çakışmalara yol açar.**

---

## 🎭 Metot Ezme (Override) — (@Override)

Child sınıf, Parent’ten gelen bir metodu **kendine göre yeniden yazabilir.**

```java
public class Kedi extends Hayvan {
    @Override
    public void yemekYer() {
        System.out.println(isim + " mama yiyor...");
    }
}
```

Çalıştırınca:

```
Pamuk mama yiyor...
```

> **Aynı metot ismi + aynı parametre + farklı içerik = Override**

---

## 🔥 super Anahtar Kelimesi

`super` → Parent (üst) sınıfa erişmek için kullanılır.

### Parent’te Constructor

```java
public class Hayvan {
    public Hayvan() {
        System.out.println("Hayvan oluşturuldu");
    }
}
```

### Child’ta

```java
public class Kedi extends Hayvan {
    public Kedi() {
        super(); // Parent constructor çağırılır
        System.out.println("Kedi oluşturuldu");
    }
}
```

Çıktı:

```
Hayvan oluşturuldu
Kedi oluşturuldu
```

---

## 🧩 Kısaca Özet

| Kavram                  | Açıklama                   |
| ----------------------- | -------------------------- |
| **extends**             | Kalıtım sağlar             |
| **Child (Subclass)**    | Miras alan sınıf           |
| **Parent (Superclass)** | Miras veren sınıf          |
| **@Override**           | Metot ezme                 |
| **super**               | Parent’ın öğelerine erişim |
