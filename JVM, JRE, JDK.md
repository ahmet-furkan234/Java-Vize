## ☕ Java Ekosistemi

Java ile çalışırken 3 temel kavram görürüz: **JDK**, **JRE**, **JVM**

---

### 1) **JVM (Java Virtual Machine)**

> “Java kodunu çalıştıran sanal makine.”

- Senin yazdığın `.java` kodu önce `.class` (bytecode) haline gelir.
- **JVM**, bu bytecode'u işletim sistemine uygun makine koduna çevirip çalıştırır.
- JVM sayesinde Java **her platformda** çalışır → _“Write Once, Run Anywhere”_.

**Görevi:** Bytecode → Makine kodu  
**Özet:** Çalıştırıcı motor.

---

### 2) **JRE (Java Runtime Environment)**

> “Java programlarını **çalıştırmak** için gerekli ortam.”

İçinde:

- **JVM**
- Java **kütüphaneleri** (java.lang, java.io, java.util…)
- Çalışma zamanında gerekli dosyalar

**JRE = JVM + Standart Kütüphaneler**

**Özet:** Java uygulamasını _çalıştırmak_ için gerekli ortamdır.  
_(Kod yazmazsın, sadece çalıştırırsın.)_

---

### 3) **JDK (Java Development Kit)**

> “Java uygulaması **geliştirmek** için gerekli paket.”

İçinde:

- **JRE**
- Derleyici (**javac**)
- Test araçları
- Debug araçları

**JDK = JRE + Derleyici ve Geliştirme Araçları**

**Özet:** Java kodu _yazmak ve derlemek_ için kullanılır.

---

## 🔥 Kısa Özet Tablosu

|Kavram|İçinde Ne Var?|Ne İşe Yarar?|Kullanım|
|---|---|---|---|
|**JVM**|Sadece Sanal Makine|Bytecode’u makine koduna çevirir|Çalıştırır|
|**JRE**|JVM + Kütüphaneler|Java programlarını çalıştırır|Kullanıcı tarafı|
|**JDK**|JRE + Derleyici + Araçlar|Java programı geliştirmeyi sağlar|Developer tarafı|

---

## 🎯 En Net Cümle

> **Program yazmak için JDK gerekir.**  
> **Programı çalıştırmak için JRE gerekir.**  
> **Çalıştırmayı yapanın kendisi JVM’dir.**