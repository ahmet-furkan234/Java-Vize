
# ✅ `stream()` Nedir?

`stream()` metodu, **koleksiyonları (List, Set, Queue)** **Stream API** ile işlem yapabileceğimiz **akış (Stream)** yapısına dönüştürür.

Yani:

```
List / Set / Collection  →  Stream
```

**Stream oluşturmadan** `filter()`, `map()`, `sorted()`, `reduce()` gibi **ara işlemler kullanılamaz**.

---

# ✅ Kullanım Şekli

```java
collection.stream()
```

---

# ✅ Nerelerde Kullanılır?

|Yapı|`stream()` var mı?|Açıklama|
|---|---|---|
|**List**|✔ Var|En sık kullanım|
|**Set**|✔ Var|Sırasız ama stream çalışır|
|**Queue**|✔ Var|Akışa çevrilir|
|**Map**|❌ Doğrudan Yok|Ama `entrySet()`, `keySet()`, `values()` ile stream edilir|

---

# ✅ Örnek 1 — List Üzerinde Kullanım

```java
List<Integer> numbers = List.of(1, 2, 3, 4, 5);

numbers.stream()               // → Stream<Integer>
       .filter(n -> n % 2 == 0)
       .forEach(System.out::println);
```

---

# ✅ Örnek 2 — Set Üzerinde Kullanım

```java
Set<String> names = Set.of("Ahmet", "Mehmet", "Ayşe");

names.stream()
     .map(String::toUpperCase)
     .forEach(System.out::println);
```

---

# ✅ Örnek 3 — Queue Üzerinde Kullanım

```java
Queue<String> q = new LinkedList<>(List.of("A", "B", "C"));

q.stream()
 .forEach(System.out::println);
```

---

# ✅ Map İçin `stream()`

Map’te **direkt** `stream()` YOK.

Ama 3 şekilde stream’e dönüştürülebilir:

|Amaç|Kullanım|Tür|
|---|---|---|
|Anahtarları stream|`map.keySet().stream()`|`Stream<K>`|
|Değerleri stream|`map.values().stream()`|`Stream<V>`|
|Hem key hem value|`map.entrySet().stream()`|`Stream<Map.Entry<K,V>>`|

### Örnek

```java
Map<String, Integer> map = Map.of("Ahmet", 25, "Ayşe", 30);

map.entrySet().stream()
   .filter(e -> e.getValue() > 26)
   .forEach(System.out::println);
```

---

# 🧠 `stream()` Ne Yapmaz?

|Yapmaz|Açıklama|
|---|---|
|Veriyi değiştirmez|Orijinal List/Set aynı kalır|
|Elemanları kopyalamaz|Hafif bir görünüm (view) oluşturur|
|İş yükü oluşturmaz|İşlem ancak terminal metotta yapılır|

Yani `stream()` sadece **akışı başlatır**, **işlemi yapmaz**.

---

# 🔚 Terminal İşlemi Olmadan Çalışmaz Örneği

```java
numbers.stream().filter(n -> n > 2); 
```

Bu **hiçbir şey yapmaz** çünkü **forEach / collect / count / reduce** yok.

Doğru:

```java
numbers.stream()
       .filter(n -> n > 2)
       .forEach(System.out::println);
```

---

# 🎯 Sonuç Net

|Nokta|Açıklama|
|---|---|
|`stream()` = Koleksiyonu Stream’e dönüştürür||
|Stream olmadan ara işlemler çalışmaz||
|`stream()` veri yapısını değiştirmez||
|Map’te doğrudan yok, entrySet/keySet/values ile kullanılır||
