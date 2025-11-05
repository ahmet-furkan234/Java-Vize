
## 🔥 `forEach()`

Akışı sonlandırır — genelde **çıktı/log** için.

```java
list.stream()
    .forEach(System.out::println);
```

### Sıra garantisi gerekirse:

```java
list.parallelStream()
    .forEachOrdered(System.out::println);
```

---

## 🔥 `toList()`

Stream → değiştirilmez (immutable) **List**.

```java
List<String> result = list.stream()
    .filter(s -> s.length() > 3)
    .toList();
```

> `add()`, `remove()` çalışmaz → veri bütünlüğü korunur.

---

## 🔥 `toSet()`

```java
Set<Integer> set = numbers.stream()
    .filter(n -> n % 2 == 0)
    .toSet();
```

---

## 🔥 `toMap()`

Eğer anahtarlar **benzersiz** ise:

```java
Map<Integer, String> map = list.stream()
    .toMap(String::length, s -> s);
```

Anahtar çakışması olabilecek durumda:

```java
Map<Integer, String> map = list.stream()
    .collect(java.util.stream.Collectors.toMap(
        String::length,
        s -> s,
        (oldVal, newVal) -> oldVal // çakışırsa eskisini tut
    ));
```

---

## 🔥 `reduce()`

Tüm değerleri **tek değere indirger**.

Toplama:

```java
int sum = numbers.stream()
    .reduce(0, Integer::sum);
```

En yaygın kullanım:

```java
int totalLength = words.stream()
    .mapToInt(String::length)
    .sum();
```

---

## 🔥 `count()`

```java
long count = numbers.stream()
    .filter(n -> n > 10)
    .count();
```

---

## 🔥 `min()` & `max()`

```java
int min = numbers.stream()
    .min(Integer::compare)
    .orElseThrow();

Person oldest = people.stream()
    .max(java.util.Comparator.comparing(Person::age))
    .orElseThrow();
```

---

## 🔥 `anyMatch() / allMatch() / noneMatch()`

```java
boolean has10 = numbers.stream().anyMatch(n -> n == 10);
boolean allPositive = numbers.stream().allMatch(n -> n > 0);
boolean noneNegative = numbers.stream().noneMatch(n -> n < 0);
```

→ **Kısa devre** yaparlar → hızlıdır.

---

## 🔥 `findFirst()` & `findAny()`

```java
var first = list.stream().findFirst().orElse(null);
var any   = list.parallelStream().findAny().orElse(null);
```

---

# 🎯 **Akılda Kalması Gereken Kural**

```java
stream()
   .filter(...)   // ara işlem
   .map(...)      // ara işlem
   .sorted()      // ara işlem
   .toList();     // ✅ terminal işlem → sonuç burada üretilir
```

---

# ⚡ Hemen Uygulama (Kendin Yap)

```java
List<String> data = List.of("ankara", "izmir", "adana", "istanbul", "antalya");

List<String> result =
    data.stream()
        .filter(s -> s.startsWith("a"))
        .map(String::toUpperCase)
        .sorted()
        .toList();

System.out.println(result);
```

**Beklenen çıktı:**

```
[ADANA, ANKARA, ANTALYA]
```
