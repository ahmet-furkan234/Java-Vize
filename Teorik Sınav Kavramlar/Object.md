## 🎯 **Nesne (Object) Nedir?**

**Nesne**, **gerçek hayattaki bir varlığın** (ör: araba, öğrenci, banka hesabı, telefon) **programlama dünyasındaki temsilidir.**

Bir nesne iki ana özellik taşır:

| Kavram                          | Açıklama                       | Örnek                               |
| ------------------------------- | ------------------------------ | ----------------------------------- |
| **State (Durum / Özellik)**     | Nesnenin sahip olduğu bilgiler | Arabanın rengi, modeli, hızı        |
| **Behavior (Davranış / İşlev)** | Nesnenin yapabildiği işler     | Araba hızlanır, durur, sinyal verir |

---

## 🧱 Class (Sınıf) ve Object (Nesne) İlişkisi

- **Class** = Nesnenin **taslağı** / şablonu
- **Object** = O şablondan **üretilmiş gerçek varlık**

**Örn:**
“Araba” bir **class** ise,
“Ali’nin kırmızı BMW’si” bir **object**’tir.

---

## ✅ Basit Bir Sınıf Oluşturalım

```java
public class Araba {
    String marka;
    String renk;
    int hiz;

    public void hizlan() {
        hiz += 10;
        System.out.println("Araba hızlandı: " + hiz);
    }

    public void dur() {
        hiz = 0;
        System.out.println("Araba durdu.");
    }
}
```

---

## 🧍‍♂️ Bu Sınıftan Nesne Oluşturalım

```java
public class Main {
    public static void main(String[] args) {
        Araba a1 = new Araba();   // Nesne oluşturma
        a1.marka = "BMW";
        a1.renk = "Kırmızı";
        a1.hiz = 0;

        a1.hizlan();
        a1.hizlan();
        a1.dur();
    }
}
```

### Çıktı:

```
Araba hızlandı: 10
Araba hızlandı: 20
Araba durdu.
```

---

## 🔍 new Anahtar Kelimesi Ne İş Yapar?

`new` → Bellekte nesne için yer açar ve nesneyi **oluşturur**.

```java
Araba a1 = new Araba();
```

- `Araba` → Tür (class)
- `a1` → Referans (nesnenin adresini tutar)
- `new Araba()` → Nesnenin kendisi

---

## 🧠 Neden Nesne Kullanıyoruz?

| Avantaj                           | Açıklama                                    |
| --------------------------------- | ------------------------------------------- |
| **Kod tekrarını azaltır**         | Nesneler tekrar tekrar üretilebilir         |
| **Düzen sağlar**                  | Kodlar mantıklı bir şekilde organize edilir |
| **Gerçek hayata yakın bir model** | Programı anlamak ve geliştirmek kolaylaşır  |
| **Bakım kolaylığı sağlar**        | Hataları bulmak ve düzeltmek kolaydır       |
