# 🧬 Liskov Substitution Principle (LSP)

**(Liskov Yerine Geçme İlkesi)**

> **Bir alt sınıf (child), üst sınıfın (parent) yerine _hiçbir şey bozulmadan_ kullanılabilmelidir.**

Yani:

- `Child`, `Parent` ile **aynı davranışı sürdürebilmeli**.
- Alt sınıf **üst sınıfın sözünü bozmayacak.**

---

## 🚨 Özet Cümle (Aklında Kalsın)

> **Child sınıf, Parent gibi davranmalıdır — sürpriz davranış olmamalı.**

Eğer alt sınıf **farklı çalışır / hata verir / metodun anlamını değiştirirse**, **LSP ihlal edilir** ❌

---

## ❌ Kötü Örnek (LSP İhlali)

### Parent sınıf

```java
public class Dikdortgen {
    protected int genislik;
    protected int yukseklik;

    public void setGenislik(int g) { this.genislik = g; }
    public void setYukseklik(int y) { this.yukseklik = y; }

    public int alan() { return genislik * yukseklik; }
}
```

### Child sınıf

```java
public class Kare extends Dikdortgen {

    @Override
    public void setGenislik(int g) {
        super.genislik = g;
        super.yukseklik = g; // KARE mantığı gereği ikisi eşit
    }

    @Override
    public void setYukseklik(int y) {
        super.genislik = y;
        super.yukseklik = y;
    }
}
```

### Kullanım

```java
Dikdortgen d = new Kare();
d.setGenislik(5);
d.setYukseklik(10);

System.out.println(d.alan());  // BEKLENEN: 50 — GERÇEK: 100 ❌
```

### **Problem:**

Kullanıcı _dikdörtgen gibi_ davranmasını bekliyor ama kare **kuralları bozdu**.
İşte **LSP ihlali** oluştu.

---

## ✅ LSP’ye Uygun Çözüm

→ Kare ve Dikdörtgen **miras ilişkisi kurmamalı**
→ İkisi de **ortak bir interface veya abstract class** uygulamalı

### Ortak arayüz:

```java
public interface Sekil {
    int alan();
}
```

### Dikdörtgen artık bağımsız:

```java
public class Dikdortgen implements Sekil {
    private int genislik;
    private int yukseklik;

    public Dikdortgen(int g, int y) {
        this.genislik = g;
        this.yukseklik = y;
    }

    public int alan() { return genislik * yukseklik; }
}
```

### Kare de bağımsız:

```java
public class Kare implements Sekil {
    private int kenar;

    public Kare(int kenar) {
        this.kenar = kenar;
    }

    public int alan() { return kenar * kenar; }
}
```

### Kullanım:

```java
public class Main {
    public static void main(String[] args) {

        Sekil s1 = new Dikdortgen(5, 10);
        Sekil s2 = new Kare(5);

        System.out.println(s1.alan());
        System.out.println(s2.alan());
    }
}
```

✅ **Artık her şekil doğru davranıyor.**

---

## 🧠 LSP Kuralını Kontrol Etme Soruları

Bir child sınıf:

| Soru                                            | Açıklama         |
| ----------------------------------------------- | ---------------- |
| Parent’ın yapabildiğini yapabiliyor mu?         | ✅ Olmalı        |
| Parent’ın davranışını _değiştiriyor_ mu?        | ❌ O zaman ihlal |
| Ekstra validasyon, kısıtlama, yasak ekliyor mu? | ❌ O zaman ihlal |
| Kullanıcıya sürpriz sonuç veriyor mu?           | ❌ O zaman ihlal |

---

## 🎯 Kısa Özet

| İlke    | Anlamı                                       |
| ------- | -------------------------------------------- |
| **SRP** | Bir sınıfın tek sorumluluğu olmalı           |
| **OCP** | Yeni özellik → yeni kod, mevcut kod bozulmaz |
| **LSP** | Alt sınıf üst sınıfın davranışını bozmaz     |
