Bunlar **Stream’i sonlandırır** ve **gerçek sonucu üretir**.  
Bu noktada **artık akış çalışmaya başlar** (lazy evaluation biter).

---

# ✅ Terminal İşlemler (Tam Liste + Kısa Açıklama + Mini Örnek)

|Metod|Ne Yapar?|Dönen Tip|
|---|---|---|
|**forEach()**|Elemanları işler / yazdırır|`void`|
|**forEachOrdered()**|Paralel akışta sıralı çıktı|`void`|
|**toList()**|Stream’i **immutable List** haline döndürür|`List<T>`|
|**toSet()**|Stream’i **immutable Set** haline döndürür|`Set<T>`|
|**toMap()**|Stream’i **immutable Map** haline döndürür|`Map<K,V>`|
|**reduce()**|Tüm elemanları katlar (toplama, çarpma vs)|`T` veya `Optional<T>`|
|**count()**|Eleman sayısını döndürür|`long`|
|**min() / max()**|En küçük / en büyük eleman|`Optional<T>`|
|**anyMatch()**|En az bir eleman koşulu sağlarsa|`boolean`|
|**allMatch()**|Tüm elemanlar sağlıyorsa|`boolean`|
|**noneMatch()**|Hiçbiri sağlamıyorsa|`boolean`|
|**findFirst()**|İlk uygun elemanı döndürür|`Optional<T>`|
|**findAny()**|Rastgele bir uygun eleman döndürür|`Optional<T>`|
