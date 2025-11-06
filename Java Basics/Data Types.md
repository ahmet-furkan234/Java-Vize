
Java’da veri tipleri **2 ana gruba ayrılır:**

1. **Primitive Types** (ilkel / temel tipler)
2. **Reference Types** (referans tipler)

---

## 1) **Primitive Types (İlkel Veri Tipleri)**

> Hafızada **doğrudan değeri** saklar.

| Tip         | Boyut  | Örnek Değer       | Açıklama                       |
| ----------- | ------ | ----------------- | ------------------------------ |
| **byte**    | 1 byte | -128 → 127        | Küçük tam sayılar              |
| **short**   | 2 byte | -32768 → 32767    | Orta boy tam sayılar           |
| **int**     | 4 byte | ~2 milyar         | En sık kullanılan tam sayı     |
| **long**    | 8 byte | Çok büyük sayılar | Sonuna `L` eklenir             |
| **float**   | 4 byte | 3.14f             | Sonuna `f` eklenir             |
| **double**  | 8 byte | 3.141592          | Varsayılan ondalıklı sayı tipi |
| **char**    | 2 byte | `'A'`, `'9'`      | Tek karakter                   |
| **boolean** | 1 bit  | `true` / `false`  | Mantıksal tip                  |

### Örnek:

```java
int yas = 25;
double maas = 10500.75;
char harf = 'A';
boolean aktif = true;
```

---

## 2) **Reference Types (Referans Tipler)**

> Hafızada **adres tutar** → Değer başka bir yerde saklanır.

|Tip|Örnek|
|---|---|
|**String**|`"Java"`|
|**Array**|`{1,2,3}`|
|**Class**|`new Student()`|
|**Interface**|`Runnable`|

### Örnek:

```java
String isim = "Ahmet";
int[] sayilar = {1, 2, 3, 4};
```

---

# 🔥 Primitive vs Reference Farkı

|Özellik|Primitive|Reference|
|---|---|---|
|Hafıza Yönetimi|Stack|Stack + Heap|
|Saklanan|Doğrudan değer|Adres (referans)|
|Varsayılan değer|0, 0.0, false|null|

### Örnek Karşılaştırma

```java
int a = 5;
int b = a;
a = 10;
System.out.println(b); // 5 (kopyalandı, değişmedi)

String x = "Java";
String y = x;
x = "Kotlin";
System.out.println(y); // Java (referans farklı oldu)
```

---

# 🎯 Özet

|Kavram|Açıklama|
|---|---|
|**Primitive Types**|Değeri direkt saklar → hızlıdır|
|**Reference Types**|Hafızada adres tutar → nesneler için kullanılır|
|**String**|Bir referans tiptir, özel davranır|
|**int** en sık kullanılan sayı tipidir|**double** ise ondalıklı sayılar içindir|
