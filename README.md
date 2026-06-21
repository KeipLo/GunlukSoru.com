# Product Requirement Document (PRD)

# GünlükSoru.com

## 1. Üst Bilgiler (Metadata)

| Alan           | Değer                                                         |
| -------------- | ------------------------------------------------------------- |
| Proje Adı      | GünlükSoru.com                                                |
| Ürün Tipi      | Mobil Öncelikli Web Uygulaması                                |
| Doküman Sahibi | Proje Kurucusu / Ürün Sahibi                                  |
| Durum          | Taslak (Geliştirmeye Hazır)                                   |
| Hedef Kitle    | Türkiye'de YKS (TYT/AYT) hazırlanan lise ve mezun öğrencileri |

### Teknoloji Yığını (Tech Stack)

| Katman         | Teknoloji                         |
| -------------- | --------------------------------- |
| Frontend       | React.js + Vite                   |
| Backend        | Express.js + TypeORM              |
| Veritabanı     | Neon DB (PostgreSQL)              |
| Dosya Depolama | AWS S3 (Soru ve Çözüm Görselleri) |

---

# 2. Amaç, Vizyon ve Değer Önerisi

## 2.1 Problem Tanımı

YKS gibi uzun soluklu sınav hazırlık süreçlerinde öğrencilerin en büyük problemi soru çözme alışkanlığı kazanamamak ve süreklilik sağlayamamaktır.

Öğrenciler genellikle yüksek motivasyonla başlayıp kısa sürede çalışmayı bırakmakta veya gün içerisindeki kısa boşlukları (otobüs, metro, sıra bekleme vb.) verimsiz geçirmektedir.

---

## 2.2 Değer Önerisi (Value Proposition)

GünlükSoru.com her gün tüm Türkiye'deki YKS öğrencilerinin karşısına tek ve ortak bir **"Günün Sorusu"** çıkarır.

Platform;

* Snapchat benzeri **Streak (Günlük Seri)** mekanizması kullanır.
* Kullanıcıların her gün geri dönmesini teşvik eder.
* Arkadaşlar arasında sosyal rekabet oluşturur.
* "Bugünkü soruyu çözdün mü?" etkisiyle akran motivasyonu yaratır.
* Gün içerisindeki kısa boşlukları verimli öğrenme seanslarına dönüştürür.

---

## 2.3 Başarı Kriterleri (KPIs)

### Retention

* D1 Retention ≥ %50
* Kayıt olan kullanıcıların en az %50'si ertesi gün tekrar giriş yapmalı ve günün sorusunu görüntülemeli veya çözmelidir.

---

# 3. Kullanıcı Hikayeleri (User Stories)

### US-01

Bir YKS öğrencisi olarak, soru çözme alışkanlığı kazanmak ve otobüste geçirdiğim 10 dakikalık boşluğu değerlendirmek istiyorum; böylece ölü zamanlarımı verimli bir hazırlık sürecine dönüştürebileceğim.

### US-02

Bir kullanıcı olarak, her gün çözdüğüm sorularla streak sayımın arttığını görmek istiyorum; böylece motivasyonumu yüksek tutarak her gün siteye girmeyi alışkanlık haline getireceğim.

### US-03

Bir aday olarak, arkadaşlarımla aynı soruyu çözüp çözmediğimi yarışarak görmek istiyorum; böylece rekabet duygusuyla disiplinimi koruyabileceğim.

---

# 4. Fonksiyonel Gereksinimler

## Mobil Öncelikli Yaklaşım

Ürün tamamen **Mobile First Responsive** tasarlanacaktır.

---

# 4.1 Global Componentler

## 4.1.1 Navbar

Ekranın üst kısmında bulunur.

### Sol Taraf

* Ana Sayfa
* Günün Sorusu
* Soru Havuzu

### Sağ Taraf

#### Streak Göstergesi

* Ateş / Seri ikonu
* Güncel streak değeri
* Tooltip desteği

#### Hesap Menüsü

İçerik:

* Kullanıcı Adı
* Notlarım
* Ayarlar
* Karanlık Mod (Dark Mode Toggle)

---

## 4.1.2 Footer

Ekranın altında yer alır.

İçerik:

* İletişim Bilgileri
* Sosyal Medya Linkleri

---

# 4.2 Sayfa Gereksinimleri

## PG-01 — Sunum Sayfası (Landing Page)

**Öncelik:** P0

### İçerik

* Projenin amacı
* Streak sistemi tanıtımı
* Değer önerisi

### CTA

* "Günün Sorusunu Çöz" butonu
* PG-03'e yönlendirme

---

## PG-02 — Kullanıcı İşlemleri (Authentication)

**Öncelik:** P0

### Kayıt Ol

Alanlar:

* E-posta
* Kullanıcı Adı
* Şifre

### E-posta Doğrulama

* Doğrulama kodu gönderimi

### Giriş Yap

* E-posta veya kullanıcı adı
* Şifre

### Şifremi Unuttum

* Sıfırlama bağlantısı veya kod gönderimi

---

## PG-03 — Günün Sorusu Sayfası

**Öncelik:** P0

### Soru Alanı

* Markdown destekli içerik
* AWS S3 görselleri

### Giriş Yapmamış Kullanıcı

* Şıklar kilitli görünür
* "Giriş Yap" CTA gösterilir

### Giriş Yapmış Kullanıcı

* 5 adet şık

  * A
  * B
  * C
  * D
  * E

### Daha Önce Çözüldü Kontrolü

Eğer soru daha önce çözülmüşse:

* Şıklar gösterilmez
* Başarı mesajı gösterilir

### Yanlış Cevap Durumu

Aktif olacak butonlar:

* Tekrar Dene
* Cevabı ve Çözümü Gör

### Çözüm Alanı

Aşağıdaki durumlarda açılır:

* Doğru cevap verilirse
* Kullanıcı "Cevabı Gör" seçerse

İçerik:

* Markdown çözüm
* AWS S3 görselleri

---

## PG-04 — Dashboard

**Öncelik:** P0

Sadece giriş yapmış kullanıcılar erişebilir.

### Duyurular

* Sistem duyuruları
* Yönetici duyuruları

### Günlük Soru Takvimi

GitHub Contribution Graph benzeri görünüm.

Gösterilen bilgi:

* Hangi günlerde soru çözüldü
* Streak devamlılığı

### İstatistikler

* Ders bazlı dağılım
* Konu bazlı dağılım
* Doğru / Toplam oranı
* En uzun streak
* Toplam çözülen soru

### Leaderboard

Gösterimler:

* Global Top 5 kullanıcı
* Kullanıcının kendi sıralaması

Örnek:

> Sen 1.240. sıradasın

---

## PG-05 — Soru Havuzu

**Öncelik:** P1

LeetCode tarzı liste görünümü.

### Kolonlar

* Soru No
* Başlık
* Konu
* Zorluk
* Çözülme Durumu

### Davranış

Satıra tıklandığında ilgili soru sayfasına yönlendirilir.

---

# 5. Kapsam Dışı (Out of Scope)

## MVP'de Yer Almayacak Özellikler

* Google ile giriş vb. sosyal giriş sistemleri
* Soruyu favorileme, like/dislike atma, soruya local not ekleme
* Settings/Preferences sayfası
* Avatar yükleme
* Profil biyografisi
* Detaylı kullanıcı profili
* Reklam entegrasyonları
* AdSense entegrasyonu

---

# 6. Fonksiyonel Olmayan Gereksinimler

## 6.1 UI / UX

### Mobil Öncelikli Tasarım

Kullanıcıların yaklaşık %90'ı mobil cihazlardan gelecektir.

Desteklenecek ortamlar:

* Safari
* Chrome
* Instagram In-App Browser

### Tasarım Gereksinimleri

* Responsive
* TailwindCSS uyumlu
* CSS Grid
* Flexbox

---

## 6.2 Güvenlik ve Kimlik Doğrulama

### Şifre Güvenliği

* Şifreler plaintext tutulamaz.
* bcrypt ile hashlenir.
* Salt kullanılır.

### JWT Yapısı

#### Access Token

* Response body içinde döner.
* Ömür: 30 saniye

#### Refresh Token

* httpOnly Cookie
* Secure Cookie
* Ömür: 7 gün

Access token süresi dolduğunda sistem arka planda otomatik yenileme yapar.

---

## 6.3 Veri Analitiği

Takip edilecek bilgiler:

* Cihaz tipi
* İşletim sistemi
* Tarayıcı bilgisi

Örnek:

* Mobile / Desktop
* iOS / Android / Windows
* Safari / Chrome

---

# 7. Veri Tabanı Şemaları

## 7.1 Question Schema

```ts
{
  id: "auto_generate_int_uniqueID",

  showDate: "DD-MM-YYYY",

  title: "TYT Matematik",

  konuBasliklari: [
    "Üslü Sayılar",
    "Temel Kavramlar"
  ],

  zorluk: "Kazanım | Kolay | Orta | Zor | Uzman",

  questionMarkdown: "string",

  solutionMarkdown: "string",

  imagePaths: {
    image1: "AWS_S3_Path_1",
    image2: "AWS_S3_Path_2"
  },

  answers: [
    "A Şıkkı",
    "B Şıkkı",
    "C Şıkkı",
    "D Şıkkı",
    "E Şıkkı"
  ],

  correctAnswerIndex: 0,

  truthPercentage: "0/0"
}
```

---

## 7.2 User Schema

```ts
{
  id: "auto_generate_int_uniqueID",

  username: "unique",

  email: "unique",

  createdAt: "DD-MM-YYYY",

  passwordHash: "string",

  isVerified: false,

  longestStreak: 0,

  solvedDates: [
    "DD-MM-YYYY"
  ],

  solvedQuestions: [
    1,
    2,
    3
  ]
}
```

---

## 7.3 Analytics Schema

```ts
{
  id: "auto_generate_int_uniqueID",

  createdAt: "Date",

  device: "Mobile",

  operatingSystem: "iOS",

  browser: "Safari",

  userId: "nullable"
}
```
