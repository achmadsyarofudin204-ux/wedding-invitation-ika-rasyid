# Undangan Pernikahan Digital — Ika & Rasyid

Web undangan digital custom (Next.js) dengan countdown realtime, peta lokasi, dan panel admin untuk kelola daftar tamu + generate link & pesan WhatsApp otomatis per tamu.

## Fitur
- Halaman undangan publik dengan nama tamu otomatis dari link (`?to=Nama`)
- Countdown hari/jam/menit/detik menuju Akad Nikah
- 3 foto: mempelai wanita, mempelai pria, foto berdua
- Peta lokasi (embed Google Maps + tombol buka di Maps)
- Panel admin (`/admin`, dilindungi password) untuk:
  - Tambah/hapus daftar tamu (nama + no. WA)
  - Generate link undangan unik otomatis per tamu
  - Tombol "Kirim WA" — membuka WhatsApp dengan pesan sudah terisi otomatis

## Langkah Deploy (GitHub + Vercel, gratis)

### 1. Siapkan foto
Ganti 3 file placeholder di folder `public/` dengan foto asli kamu (nama file harus SAMA PERSIS):
- `public/foto-ika.jpg`
- `public/foto-rasyid.jpg`
- `public/foto-berdua.jpg`

### 2. Upload ke GitHub
1. Buat repository baru di github.com (gratis), misal nama `undangan-ika-rasyid`
2. Upload semua isi folder ini ke repository itu (drag-drop lewat web GitHub, atau pakai GitHub Desktop)

### 3. Deploy ke Vercel
1. Buka vercel.com, daftar/login pakai akun GitHub (gratis)
2. Klik "Add New Project", pilih repository yang tadi diupload
3. Biarkan setting default (Vercel otomatis deteksi Next.js), klik "Deploy"

### 4. Aktifkan Vercel KV (database gratis untuk data tamu)
1. Di dashboard project Vercel kamu, buka tab "Storage"
2. Klik "Create Database" → pilih "KV" (Redis)
3. Ikuti wizard-nya, hubungkan ke project ini — Vercel otomatis menambahkan environment variable `KV_*` yang dibutuhkan, kamu tidak perlu setting manual

### 5. Set password admin
1. Di dashboard project Vercel, buka Settings → Environment Variables
2. Tambahkan variable baru:
   - Name: `ADMIN_PASSWORD`
   - Value: (password pilihan kamu, buat yang kuat)
3. Redeploy project (Settings → Deployments → titik tiga di deployment terbaru → Redeploy) supaya variable baru kebaca

### 6. Selesai!
- Undangan publik: `https://nama-project-kamu.vercel.app`
- Admin panel: `https://nama-project-kamu.vercel.app/admin`
- Link per tamu otomatis dibuatkan di admin panel, formatnya: `https://nama-project-kamu.vercel.app/?to=NamaTamu`

## Custom Domain (opsional)
Kalau mau pakai domain sendiri (misal `ikarasyid.com`), tambahkan di Vercel dashboard → Settings → Domains. Domain custom butuh beli sendiri (~Rp150rb/tahun), tapi hosting-nya tetap gratis di Vercel.

## Menjalankan lokal (opsional, untuk testing sebelum deploy)
```
npm install
npm run dev
```
Buat file `.env.local` (contoh isinya ada di `.env.example`) supaya fitur admin bisa ditest lokal juga.
