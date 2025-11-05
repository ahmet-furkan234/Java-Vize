
# ✅ **1) filter()**

**Ne yapar?**  
Koşulu **sağlayan** elemanları **tutar**, diğerlerini **atar**.

```java
numbers.stream().filter(n -> n > 10);
```

---

# ✅ **2) map()**

**Ne yapar?**  
Her elemanı **dönüştürür** → başka bir değere çevirir.

```java
numbers.stream().map(n -> n * 2);
```

---

# ✅ **3) flatMap()**

**Ne yapar?**  
**Liste içindeki listeleri düzleştirir**.  
`List<List<T>>` → `Stream<T>` haline getirir.

```java
listOfLists.stream().flatMap(list -> list.stream());
```

---

# ✅ **4) distinct()**

**Ne yapar?**  
**Aynı** olan elemanları **tekrar etmeyecek** şekilde filtreler.

```java
numbers.stream().distinct();
```

---

# ✅ **5) sorted()**

**Ne yapar?**  
Elemanları **doğal sıraya göre sıralar**.

```java
numbers.stream().sorted();
```

**Özel sıralama:**

```java
numbers.stream().sorted(Comparator.reverseOrder());
```

---

# ✅ **6) limit(n)**

**Ne yapar?**  
İlk **n** elemanı alır.

```java
numbers.stream().limit(3);
```

---

# ✅ **7) skip(n)**

**Ne yapar?**  
İlk **n** elemanı atlar.

```java
numbers.stream().skip(2);
```

---

# ✅ **8) peek()**

**Ne yapar?**  
Akıştaki elemanları değiştirmeden **gözlemlemeyi/loglamayı** sağlar.  
**Genelde debug için kullanılır.**

```java
numbers.stream().peek(System.out::println);
```

---

# ✅ **9) takeWhile()** _(Java 9+)_

**Ne yapar?**  
Koşul **true olduğu sürece** elemanları alır.  
Koşul **false olunca durur**.

```java
numbers.stream().takeWhile(n -> n < 10);
```

---

# ✅ **10) dropWhile()** _(Java 9+)_

**Ne yapar?**  
Koşul **true olduğu sürece** elemanları **atlar**.  
Koşul false olunca **kalanları alır**.

```java
numbers.stream().dropWhile(n -> n < 10);
```

---

# ✅ **11) mapToInt(), mapToLong(), mapToDouble()**

**Ne yapar?**  
Stream’i **sayısal özel akışlara** çevirir (IntStream, LongStream, DoubleStream).

```java
strings.stream().mapToInt(String::length);
```

---

# ✅ **12) boxed()**

**Ne yapar?**  
`IntStream` → `Stream<Integer>` gibi **wrapper** tipe çevirir.

```java
IntStream.range(1, 5).boxed();
```

---

# 🎯 Ana Mantık (En Önemli Cümle)

> Bu metotların hepsi **yeni Stream döndürür**, **sonuç üretmez**.  
> Sonuç ancak `forEach`, `collect`, `count`, `reduce` gibi **terminal işlem** geldiğinde oluşur.

---