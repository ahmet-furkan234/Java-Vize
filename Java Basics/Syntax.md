
# ☕ Java Basic Syntax (Temel Sözdizimi)

Java’da her şey **sınıflar (class)** içinde yazılır ve programın çalışmaya başladığı nokta **`main`** metodudur.

```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello Java!");
    }
}
```

---

## 1) **Class Yapısı**

```java
public class ClassName {
    // kodlar burada
}
```

- **Dosya adı**, sınıf adıyla **aynı** olmalıdır.
    - `ClassName.java` → `public class ClassName`

---

## 2) **main Metodu**

Java uygulamasının başlangıç noktasıdır.

```java
public static void main(String[] args) { }
```

|Anahtar Kelime|Anlamı|
|---|---|
|**public**|Her yerden erişilebilir|
|**static**|Nesne oluşturmadan çalışır|
|**void**|Geri değer döndürmez|
|**String[] args**|Komut satırı argümanları|

---

## 3) **Ekrana Yazdırma**

```java
System.out.println("Yazı");
System.out.print("Yan yana");
```

- `println` → yaz + alt satıra geç
- `print` → sadece yaz

---

## 4) **Yorum Satırları**

Kod açıklamak için kullanılır, çalışmaz.

```java
// Tek satır yorum

/* 
  Çok satırlı
  yorum
*/
```

---

## 5) **Değişkenler (Variables)**

```java
int sayi = 10;
double pi = 3.14;
char harf = 'A';
boolean aktif = true;
String isim = "Ahmet";
```

|Tür|Açıklama|Örnek|
|---|---|---|
|`int`|Tam sayı|`int x = 5;`|
|`double`|Ondalık sayı|`double d = 3.2;`|
|`char`|Tek karakter|`char c = 'z';`|
|`boolean`|true/false|`boolean t = false;`|
|`String`|Metin|`String s = "Java";`|

---

## 6) **Temel Operatörler**

```java
int a = 10;
int b = 3;

System.out.println(a + b); // 13
System.out.println(a - b); // 7
System.out.println(a * b); // 30
System.out.println(a / b); // 3
System.out.println(a % b); // 1 (mod)
```

---

## 7) **Koşul Yapısı (if / else)**

```java
int yas = 18;

if (yas >= 18) {
    System.out.println("Reşit");
} else {
    System.out.println("Reşit değil");
}
```

---

## 8) **Döngüler**

### `for` döngüsü

```java
for(int i = 0; i < 5; i++){
    System.out.println(i);
}
```

### `while` döngüsü

```java
int i = 0;
while(i < 5){
    System.out.println(i);
    i++;
}
```

---

# 🎯 Özet

|Yapı|Görev|
|---|---|
|**class**|Java kodlarının bulunduğu yapı|
|**main()**|Programın başlangıç noktası|
|**System.out.println**|Ekrana çıktı verir|
|**Değişkenler**|Veri saklar|
|**if / else**|Karar yapıları|
|**for / while**|Döngü yapıları|
