# 🧩 **Interface (Arayüz) Nedir?**

**Interface**, sınıflara **ne yapmaları gerektiğini** söyleyen ama **nasıl yapacaklarını söylemeyen** bir yapıdır.

> Yani **"Ne yapılacak?"** sorusunu cevaplar,
> **"Nasıl yapılacak?"** çocuk sınıfa bırakılır.

---

## 🎯 Interface’in Amacı

| Amaç                               | Açıklama                                     |
| ---------------------------------- | -------------------------------------------- |
| Ortak davranışları tanımlamak      | Sınıfların uyması gereken kuralları belirler |
| Soyutlama (Abstraction) sağlamak   | Gereksiz detayları gizler                    |
| Gevşek bağlılık (loosely coupling) | Esnek ve genişletilebilir yazılım sağlar     |

---

# ✅ Interface Nasıl Yazılır?

```java
public interface Sekil {
    void alan();   // Gövdesiz (abstract) metot
    void cevre();
}
```

Interface içindeki metotlar **varsayılan olarak abstract’tır**, `abstract` yazmana gerek yoktur.

---

# 🏗️ Interface’i Class’ta Uygulamak (implements)

```java
public class Kare implements Sekil {

    int kenar;

    public Kare(int kenar) {
        this.kenar = kenar;
    }

    @Override
    public void alan() {
        System.out.println("Alan: " + (kenar * kenar));
    }

    @Override
    public void cevre() {
        System.out.println("Çevre: " + (4 * kenar));
    }
}
```

### Kullanım:

```java
public class Main {
    public static void main(String[] args) {
        Sekil s = new Kare(5);
        s.alan();
        s.cevre();
    }
}
```

### Çıktı:

```
Alan: 25
Çevre: 20
```

---

# 🔥 Önemli Fark: `extends` vs `implements`

| Kelime       | Kullanıldığı Yer  | Açıklama                     |
| ------------ | ----------------- | ---------------------------- |
| `extends`    | Class → Class     | Kalıtım (is-a ilişkisi)      |
| `implements` | Class → Interface | Interface davranışı uygulama |

---

# 🔁 Bir Sınıf Birden Fazla Interface’i Uygulayabilir ✅

```java
public interface Ucabilir { void ucar(); }
public interface Yuruyebilir { void yuru(); }

public class Kus implements Ucabilir, Yuruyebilir {
    public void ucar() { System.out.println("Kuş uçuyor."); }
    public void yuru() { System.out.println("Kuş yürüyor."); }
}
```

> Interface → **çoklu miras** mümkündür ✅
> Class → **çoklu miras yok** ❌

---

# 🧠 Interface İçinde Neler Olabilir?

| Yapı                    | Durum                                                 |
| ----------------------- | ----------------------------------------------------- |
| abstract metot          | ✅ (varsayılan davranış)                              |
| default metot (Java 8+) | ✅ gövdeli olabilir                                   |
| static metot (Java 8+)  | ✅ gövdeli olabilir                                   |
| değişken                | ✅ **ama otomatik olarak → public static final** olur |

---

## 🏗️ default Metot Örneği (Java 8+)

```java
public interface Sekil {
    void alan();
    default void bilgi() {
        System.out.println("Ben bir şekilim.");
    }
}
```

Kullanan sınıf isterse override edebilir.

---

## 🚀 static Metot Örneği (Java 8+)

```java
public interface Sekil {
    static void merhaba() {
        System.out.println("Interface üzerinden çağrıldım.");
    }
}
```

Kullanım:

```java
Sekil.merhaba();
```

---

# 🎯 Interface vs Abstract Class

| Özellik       | Interface                | Abstract Class              |
| ------------- | ------------------------ | --------------------------- |
| Amaç          | Ne yapılmalı?            | Ne + Nasıl yapılmalı?       |
| Field         | public static final      | normal değişkenler olabilir |
| Constructor   | Yok                      | Var                         |
| Çoklu kalıtım | ✅ Var                   | ❌ Yok                      |
| Metot tipi    | Soyut + default + static | Soyut + gövdeli             |

---

# 🏁 Kısa Özet

- Interface **kuralları belirler**
- Sınıflar **implements** ile bu kuralları **uygulamak zorundadır**
- Çoklu interface uygulanabilir
- Modern interface yapısı default & static metodları destekler
