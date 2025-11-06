# 🧩 **Composition (Bileşim) Nedir?**

**Bir sınıfın**, başka bir sınıfı **içerisinde değişken olarak kullanmasıdır.**

Yani:

> **“Bir şeyin bir şeyi vardır”** ilişkisi.

**HAS-A Relationship** olarak da bilinir.

---

## 🎯 Temel Felsefe

| İlişki Türü           | Anlamı                 | Örnek                           |
| --------------------- | ---------------------- | ------------------------------- |
| Inheritance (extends) | **is-a** → “odur”      | Kedi **bir** Hayvandır          |
| Composition (has-a)   | **has-a** → “sahiptir” | Araba’nın **bir** Motoru vardır |

---

## 🧱 Örnek: Araba ve Motor

### Motor Sınıfı

```java
public class Motor {
    int motorGucu;

    public Motor(int motorGucu) {
        this.motorGucu = motorGucu;
    }

    public void calistir() {
        System.out.println("Motor çalıştı. Güç: " + motorGucu);
    }
}
```

### Araba Sınıfı — Motoru İçerir (HAS-A)

```java
public class Araba {
    private Motor motor; // Composition

    public Araba(Motor motor) {
        this.motor = motor;
    }

    public void arabayiCalistir() {
        motor.calistir(); // Motorun davranışını kullanır
        System.out.println("Araba harekete geçti.");
    }
}
```

### Kullanım

```java
public class Main {
    public static void main(String[] args) {

        Motor m = new Motor(120);
        Araba a = new Araba(m);

        a.arabayiCalistir();
    }
}
```

### Çıktı:

```
Motor çalıştı. Güç: 120
Araba harekete geçti.
```

---

## 🎯 Composition Neden Önemli?

| Avantaj                               | Açıklama                                     |
| ------------------------------------- | -------------------------------------------- |
| **Daha esnek yapı sağlar**            | İstediğimiz bileşenleri rahatça değiştiririz |
| **Kod tekrarını azaltır**             | Ortak davranışları başka sınıflara aktarırız |
| **Inheritance bağımlılığını azaltır** | Gereksiz `extends` kullanımını engeller      |
| **Test edilebilirliği artırır**       | Mock / Fake bileşen eklemek kolay olur       |

---

## ❗ Composition vs Inheritance Karşılaştırması

| Özellik        | Composition            | Inheritance            |
| -------------- | ---------------------- | ---------------------- |
| Bağlılık       | **Zayıf** (daha esnek) | **Güçlü bağımlılık**   |
| Kullanım Amacı | Özellik eklemek        | Tür ilişkisi kurmak    |
| Önerilen       | ✅ Tercih edilir       | ⚠️ Sadece gerekli ise  |
| Örnek          | "Araba _motor içerir_" | "Kedi _bir hayvandır_" |

> **Kural:** > **Mümkünse composition kullan, inheritance’a mecbur kalırsan geç.**

---

## 🧠 Çok Önemli Bir Bakış Açısı

Eğer şunu diyorsan:

- **“Bu sınıf, o sınıfın bir türü (is-a) ise → Inheritance**
- **“Bu sınıf, o sınıfa sahip (has-a) ise → Composition**
