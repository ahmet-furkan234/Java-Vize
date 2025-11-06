# 🧱 **Single Responsibility Principle (SRP)**

**(Tek Sorumluluk İlkesi)**

> **Bir sınıfın yalnızca _bir tane_ sorumluluğu olmalıdır.**
> Yani **bir sınıf sadece _tek bir işi_ yapmalıdır.**

---

## 🎯 Amaç

- Sınıfları **daha basit**, **daha okunabilir** ve **daha test edilebilir** hale getirmek.
- Kodda **değişiklik yaparken yan etkileri azaltmak.**

---

## ❌ SRP İhlal Eden _Kötü Örnek_

Aşağıdaki sınıf çok fazla iş yapıyor:

```java
public class OgrenciIslemleri {

    public void ogrenciKaydet(Ogrenci ogr) {
        // Öğrenci veritabanına kaydediliyor
    }

    public void mailGonder(Ogrenci ogr) {
        // Öğrenciye hoş geldin maili gönderiliyor
    }
}
```

### Sorun:

- **Aynı sınıf hem kayıt işlemini hem e-mail işlemini yapıyor.** ❌
- Yarın mail gönderme yöntemi değişirse → sınıfı **değiştirmen gerekir** → risk artar.

---

## ✅ SRP’ye Uygun **Doğru Yapı**

Görevleri **ayırıyoruz**:

### 1) Kayıt sorumluluğu

```java
public class OgrenciKayitService {
    public void kaydet(Ogrenci ogr) {
        System.out.println("Öğrenci kaydedildi: " + ogr.ad);
    }
}
```

### 2) Bildirim (mail) sorumluluğu

```java
public class MailService {
    public void mailGonder(Ogrenci ogr) {
        System.out.println("Mail gönderildi: " + ogr.ad);
    }
}
```

### Kullanım:

```java
public class Main {
    public static void main(String[] args) {
        Ogrenci o = new Ogrenci("Ahmet");

        OgrenciKayitService kayit = new OgrenciKayitService();
        MailService mail = new MailService();

        kayit.kaydet(o);
        mail.mailGonder(o);
    }
}
```

---

# 🤝 Neden Bu Doğru?

| Avantaj            | Açıklama                                 |
| ------------------ | ---------------------------------------- |
| Kod Modülerdir     | Sorumluluklar net ayrılmıştır            |
| Değiştirmesi kolay | Mail değişirse, kayıt koduna dokunmazsın |
| Test etmek kolay   | Her sınıf tek davranışı test eder        |
| Bakım kolay        | Kod büyüdükçe yönetmesi kolaydır         |

---

## 🧠 SRP’yi Aklında Tutmak İçin Basit Cümle:

> **Bir sınıfın değişme sebebi _bir tane_ olmalıdır.**

Eğer bir sınıfın “değişme nedeni” birden fazla ise → SRP **ihlal edilmiştir**.
