## Siteye ulaşmak için: https://saintberat.github.io/goodpass/
## 🔍 GoodPass Nasıl Çalışır?

GoodPass, girilen şifreyi anlık olarak analiz eden ve güvenliğini ölçen bir web uygulamasıdır.  
Her şey tarayıcı içinde çalışır, yani şifreniz cihazınızdan dışarı çıkmaz (ihlal kontrolü hariç, o da güvenli şekilde yapılır).

---

### ⚙️ Temel Mantık

Kullanıcı şifreyi yazdıkça:

- Şifrenin karakter yapısı analiz edilir  
- Entropi hesaplanır  
- Tahmini kırılma süresi hesaplanır  
- Güç seviyesi belirlenir  
- UI anlık olarak güncellenir  

---

### 🔐 Entropi Hesaplama

Şifre gücü **entropi (bit)** üzerinden hesaplanır.

- Karakter havuzu belirlenir (küçük harf, büyük harf, sayı, özel karakter)  
- Formül: `entropy = uzunluk × log2(havuz)`  

Bu sayede şifrenin ne kadar zor kırılacağı tahmin edilir.

---

### ⏱️ Kırılma Süresi

- 10 GH/s brute-force gücü varsayılır  
- Entropiye göre süre hesaplanır  
- Sonuç kullanıcıya anlaşılır şekilde gösterilir (sn, dk, yıl vs.)

---

### 📊 Güç Seviyeleri

Şifre, entropiye göre sınıflandırılır:

- KRİTİK  
- ZAYIF  
- ORTA  
- GÜÇLÜ  
- MÜKEMMEL  

Aynı anda progress bar ve renkler güncellenir.

---

### ✅ Kural Kontrolleri

Şifre aşağıdaki kriterlere göre kontrol edilir:

- En az 8 karakter  
- Büyük harf içerme  
- Küçük harf içerme  
- Sayı içerme  
- Özel karakter içerme  
- Tekrarlayan karakter olmaması  

Her kural UI üzerinde anlık olarak işaretlenir.

---

### 👁️ Görünürlük Kontrolü

- Kullanıcı isterse şifreyi gizleyip gösterebilir  
- Bu işlem tamamen client-side yapılır  

---

### 🧨 İhlal Kontrolü

Şifre, bilinen veri sızıntılarında var mı diye kontrol edilir.

Ama olay şu:

- Şifrenin tamamı gönderilmez  
- Önce SHA-1 hash alınır  
- Sadece ilk 5 karakter API’ye gönderilir (**k-anonymity**)  
- Gelen listede eşleşme aranır  

Yani şifren “tam haliyle” hiçbir yere gitmez.

---

### 🛡️ Özet

GoodPass:

- Gerçek zamanlı analiz yapar  
- Şifre gücünü bilimsel olarak hesaplar  
- Kullanıcıyı yönlendirir  
- Güvenli şekilde ihlal kontrolü yapar  
