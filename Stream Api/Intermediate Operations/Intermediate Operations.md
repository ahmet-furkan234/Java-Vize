
Bunların hepsi **Stream’i döndürür** → yani zincirlenebilir.  
**SONUÇ ÜRETMEZLER** → terminal işlem (forEach, collect, count…) gelene kadar **çalışmazlar**.
# ✅ **ARA İŞLEMLER (Intermediate Operations)** — **Tam Liste**

|Metod|Ne Yapar?|Örnek|
|---|---|---|
|**filter()**|Elemanları koşula göre süzer|`filter(n -> n > 5)`|
|**map()**|Elemanları dönüştürür|`map(n -> n * 2)`|
|**flatMap()**|Liste içindeki listeyi düzleştirir|`flatMap(List::stream)`|
|**distinct()**|Tekrarlayanları kaldırır|`distinct()`|
|**sorted()**|Sıralama yapar|`sorted()`|
|**sorted(Comparator)**|Özel sıralama yapar|`sorted(Comparator.reverseOrder())`|
|**peek()**|Akış içinde debug/loglama yapar (değiştirmez)|`peek(System.out::println)`|
|**limit()**|İlk N elemanı alır|`limit(3)`|
|**skip()**|İlk N elemanı atlar|`skip(2)`|
|**takeWhile()**|Şart sağlanırken alır (Java 9+)|`takeWhile(n -> n < 5)`|
|**dropWhile()**|Şart sağlandığı sürece atar (Java 9+)|`dropWhile(n -> n < 5)`|
|**mapToInt(), mapToLong(), mapToDouble()**|Sayısal akışa çevirir|`mapToInt(String::length)`|
|**boxed()**|Primitive Stream → Object Stream|`mapToInt(...).boxed()`|