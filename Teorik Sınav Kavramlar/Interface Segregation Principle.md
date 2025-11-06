# 🎯 **Interface Segregation Principle (ISP)**

**Arayüz Ayrımı İlkesi**

> **Bir sınıf, kullanmadığı metotları içeren interface’i _implement etmek zorunda kalmamalıdır_.**

Yani:

- **Büyük ve şişmiş** interface'ler **yanlıştır** ❌
- Küçük, **amaç odaklı**, **özelleşmiş** interface'ler kullanılmalıdır ✅

---

## 🧩 Özet Cümle

> **Az metot içeren, odaklı interface → iyidir** > **Her şeyi içeren "God Interface" → kötüdür**

---

## ❌ Kötü Örnek (ISP İhlali)

```java
public interface Calisan {
    void calis();
    void yemekYe();
    void raporHazirla();
    void sunumYap();
}
```

Şimdi bir **Temizlik Görevlisi** sınıfı yazalım:

```java
public class TemizlikGorevlisi implements Calisan {
    public void calis() { System.out.println("Temizlik yapıyor"); }
    public void yemekYe() { System.out.println("Yemek molası"); }

    // BU İKİSİNİ YAPMAK ZORUNDA KALDI (!) ❌
    public void raporHazirla() { /* anlamsız */ }
    public void sunumYap() { /* anlamsız */ }
}
```

### Problem:

- Temizlik görevlisi _sunum yapmak zorunda DEĞİL_
- Interface **işi olduğu kadar davranış içermeli**

**İşte bu ISP’nin ihlalidir.**

---

## ✅ ISP’yi Uygulayalım (Doğru Yapı)

### 1) Interface’leri _işe göre ayır_

```java
public interface Calisabilir {
    void calis();
}

public interface YemekYiyebilir {
    void yemekYe();
}

public interface RaporHazirlayabilir {
    void raporHazirla();
}

public interface SunumYapabilir {
    void sunumYap();
}
```

### 2) Sınıflar sadece **ihtiyaç duyduğu interface’leri** implement eder

```java
public class TemizlikGorevlisi implements Calisabilir, YemekYiyebilir {
    public void calis() { System.out.println("Temizlik yapıyor"); }
    public void yemekYe() { System.out.println("Yemek molası"); }
}
```

```java
public class Muhendis implements Calisabilir, YemekYiyebilir, RaporHazirlayabilir {
    public void calis() { System.out.println("Projede çalışıyor"); }
    public void yemekYe() { System.out.println("Yemek yiyor"); }
    public void raporHazirla() { System.out.println("Rapor hazırlıyor"); }
}
```

```java
public class Yonetici implements Calisabilir, YemekYiyebilir, RaporHazirlayabilir, SunumYapabilir {
    public void calis() { System.out.println("Toplantıyı yönetiyor"); }
    public void yemekYe() { System.out.println("Yemek yiyor"); }
    public void raporHazirla() { System.out.println("Rapor yazıyor"); }
    public void sunumYap() { System.out.println("Sunum yapıyor"); }
}
```

### Artık herkes **sadece kendi işini yapıyor.** ✅

---

## 🧠 ISP’yi Kontrol Etmek İçin 3 Soru

| Soru                                                        | İdeal Cevap  |
| ----------------------------------------------------------- | ------------ |
| Bir sınıf interface’i uygularken gereksiz metot yazıyor mu? | ❌ Yazmamalı |
| Interface birden fazla amaca mı hizmet ediyor?              | ❌ Etmemeli  |
| Interface’ler _özelleştirilmiş_ ve _küçük_ mü?              | ✅ Olmalı    |

---

# 📝 Kısa Özet

| İlke    | Amaç                                                  |
| ------- | ----------------------------------------------------- |
| **ISP** | Sınıflar **kullanmadığı metotları implement etmesin** |
| Çözüm   | Büyük interface → küçük interface’lere böl            |
