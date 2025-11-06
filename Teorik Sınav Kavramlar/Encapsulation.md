# 🎯 Encapsulation (Kapsülleme) Nedir?

**Nesnenin iç verilerini koruyup**, dış dünyanın bu verilere **doğrudan erişmesini engelleme**,
ve **erişimi kontrollü metotlar (getter/setter)** ile sağlama tekniğidir.

---

## 🧱 Neden Encapsulation Kullanılır?

| Sebep                     | Açıklama                                       |
| ------------------------- | ---------------------------------------------- |
| **Veri Güvenliği**        | Dışarıdan yanlış değer atanması engellenir.    |
| **Kontrollü Erişim**      | Verilere nasıl ulaşılacağını biz belirleriz.   |
| **Kod Yönetilebilirliği** | Büyük projelerde düzenli yapı sağlar.          |
| **Değişiklik Kolaylığı**  | İç yapıyı değiştirsen bile dış kod etkilenmez. |

---

## 🔒 Nasıl Yapılır?

1. **Sınıf özellikleri (variables) → `private` yapılır**
2. **Bu özelliklere erişmek için → `get` ve `set` metotları eklenir**

---

## 👤 Örnek: Kapsüllenmemiş (Yanlış Yaklaşım)

```java
public class Ogrenci {
    public int ogrNo;
    public String ad;
}
```

Dışarıdan her yer **istediği gibi** değiştirebilir → ❌

```java
Ogrenci o = new Ogrenci();
o.ogrNo = -20; // saçma bir değer! ❌
```

---

## ✅ Doğru Yaklaşım (Encapsulation ile)

```java
public class Ogrenci {
    private int ogrNo;
    private String ad;

    public int getOgrNo() {
        return ogrNo;
    }

    public void setOgrNo(int ogrNo) {
        if (ogrNo > 0) { // Kontrol koyduk
            this.ogrNo = ogrNo;
        } else {
            System.out.println("Öğrenci numarası pozitif olmalı!");
        }
    }

    public String getAd() {
        return ad;
    }

    public void setAd(String ad) {
        this.ad = ad;
    }
}
```

---

## 🧠 Kullanımı

```java
public class Main {
    public static void main(String[] args) {
        Ogrenci o = new Ogrenci();
        o.setOgrNo(25);
        o.setAd("Ahmet");

        System.out.println(o.getOgrNo());
        System.out.println(o.getAd());
    }
}
```

### Çıktı:

```
25
Ahmet
```

---

## 🎛 Getter ve Setter Mantığı Kısa Özet

| Tür        | Görevi            | Örnek     |
| ---------- | ----------------- | --------- |
| **Getter** | Veriyi döndürür   | `getAd()` |
| **Setter** | Veriyi değiştirir | `setAd()` |

Setter’lar içinde **her zaman doğrulama yapılabilir** → işte **kapsülleme gücü** burada başlar.

---

## 🧠 Sonuç

| Özellik     | Değer                            |
| ----------- | -------------------------------- |
| Değişkenler | **private** olmalı               |
| Erişim      | **Getter/Setter** ile sağlanmalı |
| Fayda       | Veri güvenliği + kontrol         |
