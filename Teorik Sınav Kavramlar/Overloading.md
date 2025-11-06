# 🔁 **Method Overloading (Metot Aşırı Yükleme)**

**Aynı isimli metotların**, **farklı parametrelerle yeniden tanımlanmasıdır.**

> Metot adı aynı →
> Parametre listesi _farklı_ olmak zorundadır.

---

## 🎯 Neden Kullanılır?

- Kodun **okunabilirliğini artırır**
- Aynı işi yapan ama **farklı türde/düzeyde parametre** isteyen metotlarda **tek isim** kullanmayı sağlar
- Daha **temiz, düzenli** bir yapı sunar

---

## ✅ Overloading Şartları

| Kural                                | Açıklama                                                  |
| ------------------------------------ | --------------------------------------------------------- |
| Metot adı aynı olacak                | `topla()` → `topla()` ✅                                  |
| Parametre sayısı veya tipi değişmeli | (int,int) ≠ (double,double)                               |
| Dönüş tipi **önemli değildir**       | Sadece dönüş tipini değiştirerek overloading yapılamaz ❌ |

---

## ❌ Yanlış Örnek (Sadece dönüş tipi değişmiş)

```java
public int topla(int a, int b) { return a + b; }
public double topla(int a, int b) { return a + b; } // ❌ Bu overload değil
```

Compiler der: “Hangisini çağıracağım belli değil.”

---

## ✅ Doğru Örnekler

### 1) Parametre Sayısı Farklı

```java
public int topla(int a, int b) {
    return a + b;
}

public int topla(int a, int b, int c) {
    return a + b + c;
}
```

---

### 2) Parametre Tipi Farklı

```java
public double topla(double a, double b) {
    return a + b;
}
```

---

### 3) Parametre Sırası Farklı

```java
public void yaz(String ad, int yas) {
    System.out.println(ad + " - " + yas);
}

public void yaz(int yas, String ad) {
    System.out.println(yas + " - " + ad);
}
```

---

## 👨‍💻 Kullanım

```java
public class Main {
    public static void main(String[] args) {

        System.out.println(topla(5, 3));
        System.out.println(topla(5, 3, 2));
        System.out.println(topla(4.5, 6.2));
    }

    public static int topla(int a, int b) {
        return a + b;
    }

    public static int topla(int a, int b, int c) {
        return a + b + c;
    }

    public static double topla(double a, double b) {
        return a + b;
    }
}
```

### Çıktı:

```
8
10
10.7
```

---

## 🧠 Overloading Nerede Kullanılır?

| Yer              | Örnek                                            |
| ---------------- | ------------------------------------------------ |
| String işlemleri | `System.out.println()` → her türü yazdırabilir   |
| Collections      | `add()` hem tek eleman hem index’li ekleme yapar |
| Constructors     | Aynı sınıf için farklı kurulum şekilleri         |

### Constructor Overloading Örneği

```java
public class Ogrenci {
    String ad;
    int yas;

    public Ogrenci() {} // varsayılan

    public Ogrenci(String ad) {
        this.ad = ad;
    }

    public Ogrenci(String ad, int yas) {
        this.ad = ad;
        this.yas = yas;
    }
}
```

---

# 📝 Kısa Özet

| Kavram       | Overloading                             | Overriding                   |
| ------------ | --------------------------------------- | ---------------------------- |
| Amaç         | Aynı metodu farklı şekillerde kullanmak | Parent metodu yeniden yazmak |
| Zaman        | Derleme zamanı                          | Çalışma zamanı               |
| Parametreler | Farklı olmak zorunda                    | Aynı olmak zorunda           |
| Erişim       | Aynı sınıf içinde yapılır               | Kalıtımla yapılır            |
