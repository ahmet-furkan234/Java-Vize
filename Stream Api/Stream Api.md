
**Stream**, Java’da veri koleksiyonlarını **dönüştürmek**, **filtrelemek**, **sıralamak**, **hesaplamak** vb. işlemleri **daha kısa, daha temiz ve fonksiyonel** şekilde yapmayı sağlar.

Koleksiyonları **döngü ile** gezmek yerine:

`for (var item : list) {     // işlem }`

Yerine şu tarz fonksiyonel yapı kullanılır:

`list.stream()     .filter(...)     .map(...)     .collect(...);`

---

## 🧠 Temel Mantık

Stream API genelde **3 aşamada** çalışır:

|Aşama|Açıklama|Örnek Metod|
|---|---|---|
|**1. Oluşturma**|Stream oluşturulur|`stream()`, `of()`, `Arrays.stream()`|
|**2. Ara işlemler**|Veri üzerinde işlem yapılır (döndürür)|`filter()`, `map()`, `sorted()`, `limit()`|
|**3. Terminal işlemler**|Sonuç döndürülür|`collect()`, `forEach()`, `count()`, `reduce()`|

---

## 📍 Örnek Veri

`List<Integer> numbers = List.of(1, 2, 3, 4, 5, 6, 7, 8, 9);`

### 🔹 Çift Sayıları Yazdırma

`numbers.stream()        .filter(n -> n % 2 == 0)        .forEach(System.out::println);`

**filter** → Eleme  
**forEach** → Çıktı verme