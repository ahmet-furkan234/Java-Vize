# 🎯 **Abstraction (Soyutlama) Nedir?**

**Soyutlama**, bir nesnenin _ne yaptığını_ gösterip, _nasıl yaptığını_ gizlemektir.

- Kullanıcı **ne yaptığını** bilir,
- Ama **nasıl yaptığını** bilmesine gerek yoktur.

### Gerçek Hayat Örneği:

Araba sürerken:

| Kullanıcı Ne Görür? | Arkada Ne Olur?                         |
| ------------------- | --------------------------------------- |
| Direksiyonu çevirir | Motor, şanzıman, akslar hesap yapar     |
| Gaza basar          | Yakıt ateşlenir, pistonlar hareket eder |

Sen **detayları bilmeden** arabayı kullanırsın → işte **abstraction** bu.

---

## ☕ Java’da Abstraction Nasıl Yapılır?

Java’da soyutlama iki yolla uygulanır:

| Yapı               | Amaç                                          | Kullanım            |
| ------------------ | --------------------------------------------- | ------------------- |
| **abstract class** | Hem gövdesi olan hem de soyut metotlar içerir | `abstract` keyword  |
| **interface**      | Tam soyutlama sağlar (Davranış tanımı)        | `interface` keyword |

---

## 🧱 1) **Abstract Class**

### Kurallar:

- `class` önüne `abstract` yazılır.
- İçinde:

  - **abstract methods** (gövdesiz metotlar)
  - **normal methods** bulunabilir.

- **Nesnesi oluşturulamaz.**

---

### Örnek

```java
public abstract class Hayvan {
    String isim;

    public abstract void sesCikar(); // Soyut metot

    public void yemekYer() { // Normal metot
        System.out.println(isim + " yemek yiyor.");
    }
}
```

### Miras Alan Sınıf (Subclass)

```java
public class Kedi extends Hayvan {
    @Override
    public void sesCikar() {
        System.out.println(isim + " miyavlıyor.");
    }
}
```

### Kullanım

```java
public class Main {
    public static void main(String[] args) {
        Kedi k = new Kedi();
        k.isim = "Pamuk";

        k.yemekYer();
        k.sesCikar();
    }
}
```

### Çıktı:

```
Pamuk yemek yiyor.
Pamuk miyavlıyor.
```

---

## 🧩 Neden Abstract Class Kullanırız?

| Durum                                          | Kullanım                             |
| ---------------------------------------------- | ------------------------------------ |
| Ortak özellikler aynı                          | Parent (abstract) sınıfa yazılır     |
| Çocuk sınıflar davranışları farklı uyguluyorsa | abstract methods ile zorunlu kılınır |

---

## 🧱 2) **Interface** (Bir sonraki adım gibi düşünebilirsin)

Ama **şimdilik kısa bilgi:**

| abstract class                          | interface                                    |
| --------------------------------------- | -------------------------------------------- |
| Hem gövdeli hem gövdesiz metot olabilir | Tüm metotlar varsayılan olarak soyuttur      |
| “Ne + Nasıl”                            | Sadece “Ne”                                  |
| 1 tane extend                           | Birden çok interface implement edilebilir ✅ |

---

# 🔍 Abstraction Kısa Özet

| Kavram          | Açıklama                                            |
| --------------- | --------------------------------------------------- |
| Soyutlama       | Gereksiz detayları gizleme                          |
| abstract class  | Gövdesiz metotları tanımlar, gövdeliler de olabilir |
| abstract method | İçeriği olmayan metot — çocuk sınıf yazmak zorunda  |
| interface       | Tam soyutlama, yalnızca davranış tanımı             |
