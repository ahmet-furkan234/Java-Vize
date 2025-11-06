
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