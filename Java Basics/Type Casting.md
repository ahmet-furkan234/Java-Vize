# 🔄 Java Type Casting (Tip Dönüştürme)

Java’da tip dönüştürme 2’ye ayrılır:

1. **Widening (Genişletme)** → **Otomatik**
2. **Narrowing (Daraltma)** → **Manuel / Zorunlu**

---

## 1) **Widening (Automatic Type Casting)**

> Küçük tip → büyük tipe giderken **Java otomatik dönüştürür**.  
> Veri **kaybı olmaz**.

**Sıralama (küçük → büyük):**  
```java
byte → short → int → long → float → double
```

### Örnek:

```java
int sayi = 10; 
double sonuc = sayi; // otomatik dönüştü 
System.out.println(sonuc); // 10.0
```

---

## 2) **Narrowing (Explicit Type Casting)**

> Büyük tip → küçük tipe giderken **manuel dönüştürme gerekir**  
> Veri **kaybı olabilir**.

### Örnek:

```java
double deger = 10.9; 
int sonuc = (int) deger; // manuel dönüştürme
System.out.println(sonuc); // 10 (ondalık kısmı kayboldu)
```

---

# 🟢 **Widening Örnekleri**

```java
byte a = 10; 
int b = a;       // otomatik 
long c = b;      // otomatik 
float d = c;     // otomatik 
double e = d;    // otomatik
```

---

# 🔴 **Narrowing Örnekleri**

```java
int x = 300; 
byte y = (byte) x; // daraltma 
System.out.println(y); // Veri kaybı olabilir!
```