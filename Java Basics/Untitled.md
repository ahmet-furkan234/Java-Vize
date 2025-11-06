Tabii TkMatE, şimdi **Java’da tip dönüştürme (Type Conversion) için kullanılan hazır metotları** kısa ve net şekilde ekliyorum.  
Bunlar özellikle **String ↔ Number** ve **Number ↔ Number** dönüşümlerinde çok kullanılır.

---

# 🔁 **String → Primitive (Temel Tipler)**

|Hedef Tip|Metot|Örnek|
|---|---|---|
|`int`|`Integer.parseInt()`|`int x = Integer.parseInt("10");`|
|`double`|`Double.parseDouble()`|`double x = Double.parseDouble("3.14");`|
|`float`|`Float.parseFloat()`|`float x = Float.parseFloat("3.14");`|
|`long`|`Long.parseLong()`|`long x = Long.parseLong("100");`|
|`byte`|`Byte.parseByte()`|`byte x = Byte.parseByte("5");`|
|`short`|`Short.parseShort()`|`short x = Short.parseShort("20");`|
|`boolean`|`Boolean.parseBoolean()`|`boolean x = Boolean.parseBoolean("true");`|

### Örnek:

```java
String s = "123";
int sayi = Integer.parseInt(s);
```

---

# 🔁 **String → Wrapper Class (Referans Tip)**

|Tip|Metot|Örnek|
|---|---|---|
|`Integer`|`Integer.valueOf()`|`Integer x = Integer.valueOf("10");`|
|`Double`|`Double.valueOf()`|`Double x = Double.valueOf("3.14");`|
|`Boolean`|`Boolean.valueOf()`|`Boolean x = Boolean.valueOf("true");`|

### Örnek:

```java
Integer sayi = Integer.valueOf("42");
```

---

# 🔁 **Primitive → String**

|Yöntem|Örnek|
|---|---|
|`String.valueOf()`|`String s = String.valueOf(100);`|
|Sona `""` ekle|`String s = 100 + "";`|

### Örnek:

```java
int sayi = 50;
String s1 = String.valueOf(sayi);
String s2 = "" + sayi;
```

---

# 🔁 **Wrapper / Primitive Arasında (Boxing & Unboxing)**

|Tür|Örnek|Açıklama|
|---|---|---|
|**Auto Boxing**|`Integer x = 10;`|primitive → wrapper|
|**Auto Unboxing**|`int y = x;`|wrapper → primitive|

### Örnek:

```java
Integer kutu = 10; // auto boxing
int deger = kutu;  // auto unboxing
```

---

# 🔄 **Sayıdan Sayıya Dönüşüm Metotları**

Wrapper sınıflarında **xxxValue()** metotları bulunur:

|Kaynak|Metot|Hedef|
|---|---|---|
|`Integer`|`intValue()`|`int`|
|`Integer`|`doubleValue()`|`double`|
|`Double`|`intValue()`|`int`|
|`Double`|`floatValue()`|`float`|

### Örnek:

```java
Double d = 12.8;
int x = d.intValue(); // 12
```

---

# 🎯 Kısa Özet

|Dönüşüm|Kullanım|
|---|---|
|String → int|`Integer.parseInt()`|
|String → double|`Double.parseDouble()`|
|int → String|`String.valueOf()` veya `+ ""`|
|Wrapper → Primitive|`.intValue()`, `.doubleValue()`|
|Primitive → Wrapper|**Auto Boxing**|

---

Hazırsan sırada **Java Operators** konusuna geçiyoruz:  
➤ Aritmetik  
➤ Karşılaştırma  
➤ Mantıksal  
➤ Atama  
➤ Artırma/Azaltma (++/--)

**Devam edeyim mi?** 🚀