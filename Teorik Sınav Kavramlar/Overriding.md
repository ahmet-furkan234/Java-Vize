# 🔄 **Method Overriding (Metot Ezme)**

**Özet:**
Bir **child (alt sınıf)**, **parent (üst sınıf)** içinde tanımlanmış bir metodu **aynı isim, aynı parametre ve aynı dönüş tipiyle yeniden tanımlar**.

Bu sayede **davranış değiştirilir**.

---

## 🎯 Neden Overriding Kullanılır?

| Amaç                    | Açıklama                               |
| ----------------------- | -------------------------------------- |
| Davranışı özelleştirmek | Alt sınıf, kendine göre iş yapabilir   |
| Polymorphism sağlamak   | “Aynı metot → farklı davranış”         |
| Kod tekrarını azaltmak  | Ortak yapı parent’a, farklılık child’a |

---

## 🧱 Overriding Kuralları

| Kural                           | Açıklama                             |
| ------------------------------- | ------------------------------------ |
| Metot adı aynı olacak           | `sesCikar()` → `sesCikar()`          |
| Parametre listesi aynı olacak   | (int,String) ≠ (int)                 |
| Dönüş tipi aynı olacak          | void → void                          |
| Erişim belirleyici daraltılamaz | `public` metot → `private` yapılamaz |
| `@Override` tavsiye edilir      | Derleyici kontrol eder               |

---

## 🐾 Basit Örnek

### Parent Sınıf

```java
public class Hayvan {
    public void sesCikar() {
        System.out.println("Hayvan ses çıkarıyor...");
    }
}
```

### Child Sınıf (Override)

```java
public class Kedi extends Hayvan {
    @Override
    public void sesCikar() {
        System.out.println("Miyav!");
    }
}
```

### Kullanım

```java
public class Main {
    public static void main(String[] args) {
        Hayvan h = new Kedi();
        h.sesCikar(); // Kedi’nin metodu çalışır
    }
}
```

### Çıktı:

```
Miyav!
```

---

## 🧠 Neden `@Override` Kullanıyoruz?

- Yazım hatalarını engeller
- Metodun gerçekten override edildiğini garanti eder

Örn: İsim yanlış yazılsa `@Override` hata verir:

```java
@Override
public void sesCikarr() { } // ❌ derleme hatası
```

---

## 🔥 `super` ile Parent Metodu Çağırmak

Child sınıfta, parent metodunu tamamen silmek yerine **üst versiyonu da kullanabiliriz.**

```java
public class Kopek extends Hayvan {
    @Override
    public void sesCikar() {
        super.sesCikar(); // önce parent davranışı
        System.out.println("Hav!"); // sonra child davranışı
    }
}
```

### Çıktı:

```
Hayvan ses çıkarıyor...
Hav!
```

---

## 🧠 Overriding vs Overloading Kısa Özet

| Özellik         | Overriding                    | Overloading                             |
| --------------- | ----------------------------- | --------------------------------------- |
| Amaç            | Davranışı değiştirmek         | Aynı metodu farklı şekillerde kullanmak |
| Nerede yapılır? | Kalıtım ile (child vs parent) | Aynı sınıf içinde                       |
| Parametre       | Aynı olmak zorunda            | Farklı olmak zorunda                    |
| Zaman           | Runtime Polymorphism          | Compile-Time Polymorphism               |
