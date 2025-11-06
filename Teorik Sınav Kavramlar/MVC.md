# 🏛 **MVC Nedir?**

**MVC**, uygulamayı üç katmana ayırarak **düzeni, test edilebilirliği ve geliştirilebilirliği** artıran bir mimari modeldir:

| Katman         | Görev                                                           |
| -------------- | --------------------------------------------------------------- |
| **Model**      | Veri ve iş kurallarını temsil eder                              |
| **View**       | Kullanıcıya gösterilen arayüz                                   |
| **Controller** | Kullanıcı isteklerini yönetir ve Model-View arasında köprü olur |

---

# 🎨 MVC Mantığını Gerçek Hayattan Düşün

> Kullanıcı sipariş verir → Garson Controller
> Mutfak siparişi hazırlar → Model
> Garson yemeği getirir → View

Controller **kullanıcı ile model arasındaki aracıdır.**

---

# 🧱 Katmanların Görevleri

## 1) **Model**

- Veritabanı tablolarını temsil eder
- İş kuralları (business logic) buraya konur
- Validation (doğrulama) işlemleri burada yapılabilir

```java
public class Ogrenci {
    private int id;
    private String ad;
}
```

---

## 2) **View**

- Son kullanıcıya gösterilen arayüzdür.
- HTML / EJS / JSP / Blade / React ekranları olabilir.

```html
<p>Öğrencinin Adı: ${ogrenci.ad}</p>
```

---

## 3) **Controller**

- Kullanıcıdan gelen isteği alır (Request)
- Model ile çalışır
- Veriyi View'a gönderir (Response)

```java
public class OgrenciController {

    private OgrenciService service = new OgrenciService();

    public String listele() {
        List<Ogrenci> ogrenciler = service.hepsiniGetir();
        return "ogrenci-liste.jsp"; // View
    }
}
```

---

# 🧬 MVC Veri Akışı

```
Kullanıcı
   ↓ (istek)
Controller
   ↓ (Model ile konuşur)
Model (Veriye ulaşır, işler)
   ↓ (sonuç)
Controller
   ↓ (veriyi View’a gönderir)
View (Kullanıcıya sonucu gösterir)
```

---

# 🚀 Mini Proje Mantığı (Basit)

### Model

```java
public class Ogrenci {
    private int id;
    private String ad;
}
```

### Controller

```java
public class OgrenciController {
    OgrenciRepository repo = new OgrenciRepository();

    public void listele() {
        repo.findAll();
    }
}
```

### View (basit HTML)

```html
<h1>Öğrenci Listesi</h1>
```

---

# ⚖️ MVC’yi Ezberlemek İçin Kısa Cümle

| Katman         | Akılda Kalacak Cümle |
| -------------- | -------------------- |
| **Model**      | Veriyi temsil eder   |
| **View**       | Ekranı temsil eder   |
| **Controller** | Köprü görevi görür   |

---

# 🔥 Neden MVC Kullanıyoruz?

| Avantaj                   | Açıklama                                |
| ------------------------- | --------------------------------------- |
| Kod düzenli olur          | Logic ve UI karışmaz                    |
| Test etmesi kolaydır      | Model, Controller ayrı test edilir      |
| Geliştirmesi kolaydır     | Yeni View eklemek sistemden bağımsızdır |
| Ekip çalışmasına uygundur | Backend ve frontend ayrılır             |

---

# 🧩 MVC == Temiz Mimariye İlk Adım

MVC’yi doğru kuran →
**Service Layer, Repository Layer, DTO, DI, IoC** konularına kolay geçer.

Sen zaten **SOLID + IoC** temelini aldın →
Şimdi **Service & Repository Architecture**'a geçmeye hazırsın ✅
