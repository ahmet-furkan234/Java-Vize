# 🧾 **Method Signature (Metot İmzası) Nedir?**

**Metodun ismi + parametre listesi** metot imzasını oluşturur.

> Yani **metodu diğer metotlardan ayıran tek şey**, **adı ve parametre yapısıdır.**

---

## 🎯 Metot İmzasını Oluşturanlar:

| Dahil Mi? | Parça                           | Örnek                | Açıklama                 |
| --------- | ------------------------------- | -------------------- | ------------------------ |
| ✅        | **Metot Adı**                   | `topla`              | İmzanın temel kısmı      |
| ✅        | **Parametre Sayısı ve Tipleri** | `(int, int)`         | İmzayı özgün yapan kısım |
| ❌        | **Dönüş Tipi**                  | `int`                | İmzaya dahil DEĞİLDİR    |
| ❌        | **Erişim Belirleyicisi**        | `public` / `private` | İmzaya dahil DEĞİLDİR    |
| ❌        | **static / final vb.**          | -                    | İmzaya dahil DEĞİLDİR    |

---

# 💡 Formül

```
Method Signature = Method Name + Parameter List
```

---

## ✅ Örnek

```java
public int topla(int a, int b)
```

### Bu metodun **signature**’ı:

```
topla(int, int)
```

> Dönüş tipi **önemli değildir** → `int` burada imzaya dahil değil.

---

# 🔁 Method Overloading ve Method Signature

**Overloading’in temel mantığı:**
Aynı isimli metodun **farklı imzalarla** yazılabilmesidir.

### Geçerli Overloading:

```java
void yaz(int a)
void yaz(String s)
void yaz(int a, int b)
```

İmzalar:

```
yaz(int)
yaz(String)
yaz(int, int)
```

### Geçersiz Overloading (HATA):

```java
int topla(int a, int b)
double topla(int a, int b) // ❌ olmaz
```

Çünkü her ikisinin imzası:

```
topla(int, int)
```

---

# 🎭 Method Signature Overriding'de Nasıl İşler?

**Override’da signature **aynı olmak zorundadır**.**

```java
class Hayvan {
    void sesCikar() {}
}

class Kedi extends Hayvan {
    @Override
    void sesCikar() {} // ✅ Method signature aynı → overriding başarılı
}
```

```java
void sesCikar(String s) {} // ❌ Bu override değil → overloading olur
```

---

# 🔥 Özet Tablosu

| Konu                  | Signature Ne Yapıyor?       |
| --------------------- | --------------------------- |
| **Overloading**       | Signature **farklı olmalı** |
| **Overriding**        | Signature **aynı olmalı**   |
| **Dönüş Tipi**        | Signature'yı **etkilemez**  |
| **Parametre Listesi** | Signature'yı **belirler**   |
