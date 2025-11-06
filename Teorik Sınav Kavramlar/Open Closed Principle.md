# 🔒 **Open/Closed Principle (OCP) Nedir?**

**Bir sınıf / modül / fonksiyon:**

- **Genişletilmeye açık (Open for Extension)** olmalı,
- **Değiştirilmeye kapalı (Closed for Modification)** olmalıdır.

Yani:

> Yeni özellik eklemek istediğinde **mevcut kodu değiştirmeden**, **yeni kod yazarak** sistemi genişletebilmelisin.

---

## 🎯 Mantık

Kod **esnek**, **ölçeklenebilir** ve **bozulmaya karşı güvenli** olmalı.

- Yeni bir özellik için **var olan sınıfı değiştirmiyorsan → OCP uygulanmış demektir.**
- Var olan kodu **her eklemede düzenlemek zorunda kalıyorsan → OCP ihlali var.**

---

# ❌ KÖTÜ ÖRNEK (**OCP ihlali**)

```java
public class BildirimServisi {
    public void gonder(String mesaj, String tip) {
        if (tip.equals("Email")) {
            System.out.println("Email gönderildi: " + mesaj);
        } else if (tip.equals("SMS")) {
            System.out.println("SMS gönderildi: " + mesaj);
        }
    }
}
```

### Sorun:

- Yeni bir bildirim türü ekleyince (Push Notification, WhatsApp, Telegram...)
  **kodu değiştirmek zorunda kalırsın** ❌
- Her değişiklik → Hata riskini artırır ❌

---

# ✅ İYİ ÖRNEK (**OCP Uygulanmış**)

### 1) Ortak bir Interface tanımla

```java
public interface Bildirim {
    void gonder(String mesaj);
}
```

### 2) Bildirim türlerini ayrı sınıflara böl

```java
public class EmailBildirim implements Bildirim {
    public void gonder(String mesaj) {
        System.out.println("Email gönderildi: " + mesaj);
    }
}

public class SMSBildirim implements Bildirim {
    public void gonder(String mesaj) {
        System.out.println("SMS gönderildi: " + mesaj);
    }
}
```

### 3) Servis sınıfı artık **genişletilmeye açık**, **değiştirmeye kapalıdır**

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

### Kullanım:

```java
public class Main {
    public static void main(String[] args) {

        BildirimServisi servis1 = new BildirimServisi(new EmailBildirim());
        servis1.gonder("Hoş Geldiniz!");

        BildirimServisi servis2 = new BildirimServisi(new SMSBildirim());
        servis2.gonder("Kodu onaylayın.");
    }
}
```

---

## ✅ Avantajlar

| Özellik            | Açıklama                           |
| ------------------ | ---------------------------------- |
| Esneklik           | Yeni tür eklemek kolay             |
| Kod Güvenliği      | Var olan kod bozulmaz              |
| Test Edilebilirlik | Birimler ayrı ayrı test edilebilir |
| Bağımlılık Azalır  | Modüler ve temiz mimari oluşur     |

---

# 🧠 En Önemli Mesaj

> Yeni özellik eklemek → ✅ Yeni sınıf yaz
> Var olan sınıfı değiştirmek → ❌ Yapma

**İşte bu OCP’nin ruhudur.**
