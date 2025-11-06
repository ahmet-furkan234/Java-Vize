# 🏛 **Dependency Inversion Principle (DIP)**

**(Bağımlılıkların Ters Çevrilmesi İlkesi)**

> **Yüksek seviye sınıflar, düşük seviye sınıflara bağımlı olmamalıdır.**
> Her iki taraf da **soyutlamalara (interface veya abstract)** bağımlı olmalıdır.

Yani:

- **Sınıflar birbirine sıkı sıkıya bağlı olmamalı.**
- Araya **interface** koyarak **gevşek bağımlılık (loose coupling)** oluşturmalıyız.

---

## 🎯 DIP’in Amacı

| Hedef                          | Açıklama                               |
| ------------------------------ | -------------------------------------- |
| Kod bağımlılığını azaltmak     | Sınıflar birbirini _direkt_ tanımaz    |
| Sistemi esnek hale getirmek    | Yeni özellik eklemek kolay olur        |
| Test edilmesi kolay hale gelir | Mock / Fake implementasyon kolaydır    |
| Değişiklik etkisini düşürmek   | Bir modül değişince diğerleri bozulmaz |

---

## ❌ DIP İhlali (Kötü Tasarım)

```java
public class BildirimServisi {
    private EmailBildirim email = new EmailBildirim();

    public void gonder(String mesaj) {
        email.gonder(mesaj);
    }
}
```

### Sorun:

- `BildirimServisi`, **EmailBildirim'e ÇOK sıkı bağlı** (hard coupling)
- SMS eklemek istersek?

  - Sınıfı **değiştirmek zorundayız** → **OCP + DIP ihlali**

---

## ✅ DIP Uygulandı (İyi Tasarım)

### 1) Soyutlama oluştur (Interface)

```java
public interface Bildirim {
    void gonder(String mesaj);
}
```

### 2) Email Bildirim

```java
public class EmailBildirim implements Bildirim {
    public void gonder(String mesaj) {
        System.out.println("Email gönderildi: " + mesaj);
    }
}
```

### 3) SMS Bildirim

```java
public class SMSBildirim implements Bildirim {
    public void gonder(String mesaj) {
        System.out.println("SMS gönderildi: " + mesaj);
    }
}
```

### 4) Servis artık sadece _soyutlamaya bağımlı_

```java
public class BildirimServisi {
    private final Bildirim bildirim;

    public BildirimServisi(Bildirim bildirim) {
        this.bildirim = bildirim;
    }

    public void gonder(String mesaj) {
        bildirim.gonder(mesaj);
    }
}
```

### 5) Kullanım

```java
public class Main {
    public static void main(String[] args) {

        BildirimServisi s1 = new BildirimServisi(new EmailBildirim());
        s1.gonder("Hoş geldin!");

        BildirimServisi s2 = new BildirimServisi(new SMSBildirim());
        s2.gonder("Kodunuz: 1234");
    }
}
```

✅ Artık:

- Yeni bildirim türü eklemek → **Yeni sınıf yazmak** (OCP uyumlu)
- Mevcut kodu değiştirmek → **Gerek yok**
- Sistem **esnek ve genişletilebilir** 🎯

---

## 🔥 DIP’i Bir Cümlede Özetle:

> **Sınıflar birbirine değil → interface’lere bağımlı olsun.**

---

# 🎯 Tüm SOLID Özet Tablosu

| İlke                          | Açıklama                                      |
| ----------------------------- | --------------------------------------------- |
| **S** - Single Responsibility | Bir sınıfın tek sorumluluğu olmalı            |
| **O** - Open/Closed           | Yeni özellik eklenebilir, mevcut kod değişmez |
| **L** - Liskov Substitution   | Alt sınıf üst sınıfın yerine geçebilmeli      |
| **I** - Interface Segregation | Büyük interface’leri küçüklerine böl          |
| **D** - Dependency Inversion  | Sınıflar interface’lere bağımlı olmalı        |
