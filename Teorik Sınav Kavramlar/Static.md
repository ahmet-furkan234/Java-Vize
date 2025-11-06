# ⚡ `static` Nedir?

`static`, **class’a ait** olan üyeleri ifade eder.
Yani **nesneye (object) değil, sınıfa bağlıdır.**

> Nesne oluşturmadan kullanılabilir.

---

## 🎯 Static’in Özünü Akılda Tut:

| Normal (instance) değişken/metot    | static değişken/metot                 |
| ----------------------------------- | ------------------------------------- |
| Nesneye aittir                      | **Sınıfa aittir**                     |
| Her nesnenin **ayrı değeri** vardır | Tüm nesneler **ortak değer paylaşır** |
| Kullanım: `nesne.degisken`          | Kullanım: `ClassAdi.degisken`         |

---

# 🧱 1) `static` Değişken (Class Variable)

### Örnek

```java
public class Ogrenci {
    String ad;             // Nesneye ait
    static String okul = "Anadolu Lisesi"; // Sınıfa ait
}
```

### Kullanım

```java
public class Main {
    public static void main(String[] args) {

        Ogrenci o1 = new Ogrenci();
        o1.ad = "Ahmet";

        Ogrenci o2 = new Ogrenci();
        o2.ad = "Mehmet";

        System.out.println(o1.okul); // Anadolu Lisesi
        System.out.println(o2.okul); // Anadolu Lisesi

        // Static erişim şekli (Doğru kullanım)
        System.out.println(Ogrenci.okul);
    }
}
```

> **Static değişken HERKES için ortaktır.**

---

# 🔥 2) `static` Metot

Static metotlar **nesne oluşturmadan** çağrılır.

```java
public class Matematik {

    public static int topla(int a, int b) {
        return a + b;
    }
}
```

### Kullanım

```java
int sonuc = Matematik.topla(5, 3);
System.out.println(sonuc); // 8
```

> Static metodun içinde **instance değişkenine erişilemez.**
> Çünkü **static** class’a aittir, instance ise nesneye.

---

# ⚠️ Kural:

**Static metot içinde `this` ve `super` kullanılamaz.**

Çünkü:

- `this` → nesneyi temsil eder
- `super` → parent nesnesini temsil eder
  Ama static → **nesnesiz çalışır**.

---

# 🧨 3) `static` Block

Sınıf **ilk yüklendiğinde** _sadece 1 kez_ çalışır.

```java
public class Ayarlar {

    static {
        System.out.println("Uygulama başlatılıyor...");
    }
}
```

---

# 🏛 4) Static Kullanım Senaryoları

| Kullanım Yeri     | Neden?                               |
| ----------------- | ------------------------------------ |
| Ortak veriler     | Okul adı, şirket adı, sabit değerler |
| Yardımcı metotlar | Matematik işlemleri, formatlama      |
| Singleton Pattern | Tek instance yönetimi                |
| Cache / Config    | Uygulama çapında paylaşılan veriler  |

---

# 🧠 Static vs Instance Kıyas Tablosu

| Özellik                          | static                  | instance            |
| -------------------------------- | ----------------------- | ------------------- |
| Bağlı olduğu                     | Class                   | Nesne               |
| Bellekteki yeri                  | Metaspace / Method Area | Heap                |
| Kullanmak için nesne gerekir mi? | ❌ Gerekmez             | ✅ Gerekir          |
| Değer paylaşımı                  | **Ortak**               | Her nesne için ayrı |

---

# 🎮 Küçük Ama Çok Önemli Örnek

```java
public class Sayaç {
    static int sayi = 0; // ortak
    int id;              // her nesne için farklı

    public Sayaç() {
        sayi++;
        id = sayi;
    }
}
```

### Main

```java
Sayaç a = new Sayaç();
Sayaç b = new Sayaç();
Sayaç c = new Sayaç();

System.out.println(a.id); // 1
System.out.println(b.id); // 2
System.out.println(c.id); // 3
```

> Çünkü `sayi` **static** → herkes paylaşır.

---

# 📝 Kısa Özet

| Anahtar Kelime | Ne ifade eder?   |
| -------------- | ---------------- |
| `static`       | Class’a ait olan |
| `this`         | O anki nesne     |
| `super`        | Parent sınıf     |
