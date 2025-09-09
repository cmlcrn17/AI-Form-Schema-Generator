
# AI Form Schema Generator

## 🎯 Proje Amacı
Bu proje, **OpenAI API** kullanarak dinamik form şemaları üretmeyi amaçlar.  
Kullanıcı, istediği form alanlarını tarif eder (örneğin: ad, soyad, tarih, saat, plaka).  
Proje, bu tarife göre:

- **JSON formatında form alanlarını**
- **XML Schema (XSD) tanımını**
- **SQL `CREATE TABLE` scriptini**

oluşturur.  
Ayrıca, bu form verileri için bir veritabanı yapısı kurar.

---

## 🔧 Kullanılacak Teknolojiler
- Python veya Node.js
- OpenAI API
- FastAPI (Python) veya Express.js (Node.js)
- SQLite veya PostgreSQL
- JSON & XML dönüştürücü kütüphaneler

---

## 📂 Proje Yapısı
AI-Form-Schema-Generator/
│
├── src/ # Ana kaynak kod
│ ├── api/ # REST API endpointleri
│ ├── services/ # OpenAI servis entegrasyonu
│ ├── converters/ # JSON & XML dönüştürücü
│ └── db/ # SQLite/PostgreSQL bağlantısı
│
├── examples/ # Örnek çıktı dosyaları
│ ├── form.json
│ ├── form.xsd
│ └── schema.sql
│
├── README.md # Proje dökümanı
└── requirements.txt # Bağımlılıklar


---

## 🚀 Kullanım Adımları

### 1. OpenAI API Bağlantısı
- [OpenAI API Key](https://platform.openai.com/) alın.
- `.env` dosyasına ekleyin:
OPENAI_API_KEY=your_api_key_here

### 2. Form İsteği Gönderme
Kullanıcıdan bir form tarifi alınır:  
Bir form oluştur. İçerisinde ad, soyad, tarih, saat, plaka bilgisi yer alsın.

### 3. OpenAI Prompt
API’ye şu şekilde gönderilir:
Kullanıcıdan alınacak form alanlarını listele.
Alanları şu formatta ver:

JSON (alan adı, veri tipi, zorunluluk)

XML Schema (XSD)

Database alan karşılığı (SQL CREATE TABLE)

### 4. Örnek Çıktı

#### JSON
```json
{
  "form_name": "AracGirisFormu",
  "fields": [
    {"name": "ad", "type": "string", "required": true},
    {"name": "soyad", "type": "string", "required": true},
    {"name": "tarih", "type": "date", "required": true},
    {"name": "saat", "type": "time", "required": true},
    {"name": "plaka", "type": "string", "required": true}
  ]
}
XML Schema (XSD)
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="AracGirisFormu">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="ad" type="xs:string"/>
        <xs:element name="soyad" type="xs:string"/>
        <xs:element name="tarih" type="xs:date"/>
        <xs:element name="saat" type="xs:time"/>
        <xs:element name="plaka" type="xs:string"/>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
SQL Script
CREATE TABLE AracGirisFormu (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  ad TEXT NOT NULL,
  soyad TEXT NOT NULL,
  tarih DATE NOT NULL,
  saat TIME NOT NULL,
  plaka TEXT NOT NULL
);

✅ Stajyer Görev Listesi

OpenAI API bağlantısını kur

API key ile basit bir prompt gönder ve cevabı JSON olarak al.

Kullanıcıdan form isteğini al

Konsol veya basit bir web arayüzü ile.

OpenAI’den gelen cevabı dönüştür

JSON çıktıyı dosyaya yaz.

XML Schema (XSD) üret.

Veritabanı entegrasyonu

SQL CREATE TABLE scriptini çalıştır.

Kullanıcı verisini bu tabloya kaydet.

REST API geliştir

/generate-form → JSON/XML döndürür.

/save-data → Form verisini DB’ye kaydeder.

Dokümantasyon hazırla

Proje amacı, kullanım adımları, örnek çıktılar.

