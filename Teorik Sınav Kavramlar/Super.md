# 🧱 **super** Anahtar Kelimesi Nedir?

`super`, **child (alt sınıf)** içinden **parent (üst sınıf)** a erişmek için kullanılır.

> Kısaca: `super` = **Parent sınıfı**nı temsil eder.

---

## 🎯 `super` Ne İçin Kullanılır?

| Kullanım                                                | Açıklama         |
| ------------------------------------------------------- | ---------------- |
| 1) Parent sınıfın **constructor**’ını çağırmak          | `super()`        |
| 2) Parent sınıfın **özelliklerine (variables)** erişmek | `super.degisken` |
| 3) Parent sınıfın **metotlarını** çağırmak              | `super.metot()`  |

---

# 🏗️ 1) Parent Constructor’ı Çağırma

### Parent Sınıf

```java
public class Hayvan {
    String isim;

    public Hayvan(String isim) {
        this.isim = isim;
        System.out.println("Hayvan oluşturuldu: " + isim);
    }
}
```

### Child Sınıf

```java
public class Kedi extends Hayvan {

    public Kedi(String isim) {
        super(isim); // Parent constructor çağrılır
        System.out.println("Kedi oluşturuldu: " + isim);
    }
}
```

### Kullanım

```java
public class Main {
    public static void main(String[] args) {
        Kedi k = new Kedi("Pamuk");
    }
}
```

### Çıktı:

```
Hayvan oluşturuldu: Pamuk
Kedi oluşturuldu: Pamuk
```

> **Not:** `super()` **her zaman constructor’ın ilk satırında** olmalıdır.

---

# 🧠 2) Parent Değişkenine Erişim

```java
public class Hayvan {
    String tur = "Genel hayvan";
}
```

```java
public class Kedi extends Hayvan {
    String tur = "Kedi";

    public void yazdir() {
        System.out.println(tur);       // Kendi değişkeni
        System.out.println(super.tur); // Parent değişkeni
    }
}
```

### Çıktı:

```
Kedi
Genel hayvan
```

---

# 🎭 3) Parent Metodunu Çağırma (Override Durumunda)

```java
public class Hayvan {
    public void sesCikar() {
        System.out.println("Hayvan ses çıkarıyor.");
    }
}
```

```java
public class Kedi extends Hayvan {

    @Override
    public void sesCikar() {
        super.sesCikar(); // Parent metodunu çalıştır
        System.out.println("Miyav!");
    }
}
```

### Kullanım:

```java
new Kedi().sesCikar();
```

### Çıktı:

```
Hayvan ses çıkarıyor.
Miyav!
```

---

# 🧩 Kısa Özet

| Kavram           | Açıklama                            |
| ---------------- | ----------------------------------- |
| `super`          | Parent sınıfına referans            |
| `super()`        | Parent constructor çağırır          |
| `super.degisken` | Parent değişkenine erişir           |
| `super.metot()`  | Parent metodunu çağırır             |
| Yerleşim kuralı  | `super()` **her zaman ilk satırda** |
