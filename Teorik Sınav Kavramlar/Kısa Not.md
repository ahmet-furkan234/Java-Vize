# 📌 Java OOP & SOLID & UML – Kısa Özet Notları

### **1) Object (Nesne)**

Gerçek hayattaki bir varlığın programdaki karşılığıdır.
**Durum (özellik) + Davranış (metot)** içerir.

---

### **2) Class (Sınıf)**

Nesnelerin **şablonudur**. Özellikler ve metotları içerir.

---

### **3) Constructor (Yapıcı Metot)**

Nesne oluşturulduğunda çalışan özel metottur.
**İsmi sınıfla aynı olur**, **geri dönüş tipi yoktur**.

---

### **4) this**

O anki **nesneyi** temsil eder.
Değişkenleri ve metotları netleştirmede kullanılır.

---

### **5) super**

**Parent (üst) sınıfa** erişimi sağlar.
`super()` → Parent constructor’ını çağırır.

---

### **6) Encapsulation (Kapsülleme)**

Verileri korumak için özellikler **private**, erişim **getter/setter** ile yapılır.

---

### **7) Inheritance (Kalıtım / Miras)**

`extends` ile yapılır.
Child → Parent’in özellik ve metotlarını miras alır.
**is-a** ilişkisidir.

---

### **8) Polymorphism (Çok Biçimlilik)**

Aynı metot farklı nesnelerde **farklı davranır**.
Override ile sağlanır.

---

### **9) Overloading (Aşırı Yükleme)**

Aynı isimli metodun parametrelerinin farklı olmasıdır.
Signature değişir.

---

### **10) Overriding (Ezme)**

Child sınıf, parent metodunu **aynı imza ile yeniden yazar**.

---

### **11) Static**

Nesneye değil, **sınıfa ait** üyeleri ifade eder.
**Nesne oluşturmadan** erişilebilir.

---

### **12) Abstraction (Soyutlama)**

Detayları gizleyip, **ne yapılacağını** tanımlar.
**abstract class** ve **interface** ile yapılır.

---

### **13) Interface**

Sınıfların **uygulamak zorunda olduğu davranışları** tanımlar.
Bir sınıf birden fazla interface’i **implements** edebilir.

---

### **14) Composition (Bileşim)**

Bir sınıfın başka bir sınıfı **içinde tutmasıdır**.
**has-a** ilişkisi.

---

### **15) Singleton Pattern**

Bir sınıftan **yalnızca 1 nesne** oluşturulmasını garanti eder.
`private constructor + static getInstance()` kullanılır.

---

### **16) Exception Handling**

Hataları kontrol altına alma mekanizması.
`try – catch – finally`, `throw`, `throws` kullanılır.

---

### **17) Access Modifiers (Erişim Belirleyiciler)**

| Modifier      | Erişim              | Açıklama             |
| ------------- | ------------------- | -------------------- |
| **public**    | Her yerden          | En geniş             |
| **protected** | Aynı paket + miras  | Kalıtım için faydalı |
| **default**   | Aynı paket          | Paket dışına kapalı  |
| **private**   | Sadece sınıf içinde | En kısıtlı           |

---

## SOLID Prensipleri

### **18) Single Responsibility Principle (SRP)**

Bir sınıfın **tek bir sorumluluğu** olmalı.

---

### **19) Open/Closed Principle (OCP)**

Kod **genişletilmeye açık**, **değiştirilmeye kapalı** olmalı.

---

### **20) Liskov Substitution Principle (LSP)**

Child sınıf **parent’ın yerine geçebilmeli**, davranış bozulmamalı.

---

### **21) Interface Segregation Principle (ISP)**

Büyük interface'ler **küçük ve iş odaklı** olmalıdır.

---

### **22) Dependency Inversion Principle (DIP)**

Sınıflar **somut** sınıflara değil, **soyutlamalara (interface)** bağımlı olmalıdır.

---

## UML

### **23) Modelleme / UML**

Sistemi koddan önce **şemalarla düşünme** biçimi.

### **24) Class Diagram**

Sınıfları, özelliklerini, metotlarını ve ilişkilerini gösterir.

---

# ✅ Kısa Ezber Tablosu

| Konu          | Anahtar Cümle                             |
| ------------- | ----------------------------------------- |
| Class         | Şablon                                    |
| Object        | Şablondan üretilmiş veri                  |
| Constructor   | Nesne oluşturulurken çalışan metot        |
| Encapsulation | Değişkenler private, erişim getter/setter |
| Inheritance   | is-a                                      |
| Composition   | has-a                                     |
| Polymorphism  | Aynı metot farklı davranır                |
| Overloading   | Parametre değişir                         |
| Overriding    | İçerik değişir                            |
| Static        | Sınıfa ait                                |
| Interface     | Ne yapılmalı                              |
| Abstract      | Ne + kısmen nasıl                         |
| SOLID         | Temiz ve bakımı kolay yazılım             |
