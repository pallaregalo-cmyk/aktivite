# Aktivite Takibi

Node.js + Express + PostgreSQL aktivite takip uygulaması.

## Railway'e Deploy

### 1. GitHub'a yükle
```bash
git init
git add .
git commit -m "init"
git branch -M main
git remote add origin https://github.com/KULLANICI/aktivite-takip.git
git push -u origin main
```

### 2. Railway'de proje oluştur
1. [railway.app](https://railway.app) → **New Project**
2. **Deploy from GitHub repo** → repoyu seç
3. Sol menü → **+ New** → **Database** → **PostgreSQL** ekle
4. PostgreSQL servisine tıkla → **Variables** sekmesi → `DATABASE_URL` değerini kopyala
5. Uygulama servisine tıkla → **Variables** → `DATABASE_URL` değişkenini yapıştır

> Railway çoğu zaman `DATABASE_URL`'yi otomatik inject eder, kontrol et.

### 3. Deploy
Railway her `git push` sonrası otomatik deploy eder.

## Lokal Geliştirme
```bash
# .env dosyası oluştur
echo "DATABASE_URL=postgresql://user:pass@localhost:5432/aktivite" > .env

npm install
node server.js
```

## API Uç Noktaları
| Metod | Yol | Açıklama |
|-------|-----|---------|
| GET | /api/logs | Logları listele (filtreli) |
| POST | /api/logs | Tek kayıt ekle |
| POST | /api/logs/bulk | Toplu kayıt ekle |
| DELETE | /api/logs/:id | Kayıt sil |

### GET /api/logs Query Parametreleri
- `start` — başlangıç tarihi (YYYY-MM-DD)
- `end` — bitiş tarihi (YYYY-MM-DD)
- `firma` — firma adı (kısmi eşleşme)
- `modul` — modül adı (kısmi eşleşme)
