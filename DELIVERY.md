# DELIVERY.md

## 👨‍🎓 Öğrenci Bilgileri

- İsim: [Ad Soyad]
- Numara: [Öğrenci Numarası]
- Ders: Açık Kaynak Kodlu Yazılımlar

---

## 📝 API Açıklaması

Bu API, bir üniversiteye ait çevrim içi kütüphane sistemini tanımlamaktadır. OpenAPI 3.0.3 standardına uygun olarak hazırlanmıştır.

### 📦 Varlıklar (Entities)

API'de aşağıdaki üç temel varlık bulunmaktadır:

1. **books** – Kitap bilgilerini içerir.
2. **students** – Öğrenci bilgilerini içerir.
3. **loans** – Ödünç alma ve iade süreçlerini yönetir.

### 🔄 CRUD İşlemleri ve Endpoint'ler

- **Books**
  - `GET /books`: Tüm kitapları listeler (sayfalama destekli)
  - `GET /books/{id}`: Belirli bir kitabı getirir
  - `POST /books`: Yeni kitap ekler
  - `PUT /books/{id}`: Mevcut kitabı günceller
  - `DELETE /books/{id}`: Kitabı siler

- **Students**
  - `GET /students`, `GET /students/{id}`
  - `POST /students`
  - `PUT /students/{id}`
  - `DELETE /students/{id}`

- **Loans**
  - `GET /loans`, `GET /loans/{id}`
  - `POST /loans`: Kitap ödünç alma
  - `PATCH /loans/{id}/return`: Kitap iade etme

### 🧱 Bileşen Kullanımı

- `components/schemas`: `Book`, `Student` ve `Loan` modelleri detaylıca tanımlanmıştır.
  - `format`, `enum`, `nullable`, `required` alanları kullanılmıştır.
- `parameters`: 
  - `path` parametreleri (`{id}`) ve
  - `query` parametreleri (`page`, `size`) kullanılmıştır.
- `responses`: 
  - 200, 201, 204, 404 yanıtlara yer verilmiştir.
  - `400` ve `500` hataları için `components > responses` kısmı tanımlıdır.

### 📄 Sayfalama ve Hatalar

- **Sayfalama**: `GET /books` endpointinde `page` ve `size` parametreleriyle uygulanmıştır.
- **Hata Durumları**: 
  - `404 Not Found`: Kaynak bulunamadığında döner.
  - `400 Bad Request`: Eksik veya geçersiz veri girildiğinde döner.
  - `500 Server Error`: Genel sunucu hatası tanımlanmıştır.

---

## 🧪 Test Notları (Opsiyonel)

Swagger Editor üzerinden yapılan bazı testler:

### ✅ `GET /books` Çağrısı
```json
{
  "books": [
    {
      "id": "123e4567-e89b-12d3-a456-426614174000",
      "title": "Sefiller",
      "author": "Victor Hugo",
      "isbn": "9781234567897",
      "publisher": "Can Yayınları",
      "pageCount": 480,
      "stock": 5
    }
  ]
}
