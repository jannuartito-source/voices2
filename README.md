# Database Suara Voice Promax

Repo ini berisi suara siap pakai yang muncul di tab **TTS**, **Ekspresi**, dan
**Podcast** pada Studio Engine.

> Repo ini **harus Public**. Colab mengambil file suara lewat
> `raw.githubusercontent.com` tanpa login, dan alamat itu hanya bisa dibuka kalau
> repo-nya Public.
>
> Tidak ada nilai rahasia di sini — kode gateway dan notebook ada di repo terpisah
> yang tetap Private.


## Isi saat ini

15 suara sudah terdaftar:

| Nama | Bahasa | Gender | Transkrip |
|---|---|---|---|
| Agung | Indonesia | Pria | tanpa (dibaca ASR) |
| Alek | Indonesia | Pria | tanpa (dibaca ASR) |
| Dono | Indonesia | Pria | tanpa (dibaca ASR) |
| Jono | Indonesia | Pria | tanpa (dibaca ASR) |
| Siti | Indonesia | Wanita | ada |
| English Female | Inggris | Wanita | ada |
| English Female 2 | Inggris | Wanita | ada |
| Anime Girl | Inggris | Wanita | ada |
| Game Announcer | Inggris | Pria | ada |
| Arabic Female | Arab | Wanita | ada |
| French Female | Prancis | Wanita | ada |
| German Male | Jerman | Pria | ada |
| Japanese Male | Jepang | Pria | ada |
| Korean Female | Korea | Wanita | ada |
| Spanish Male | Spanyol | Pria | ada |

Empat suara Indonesia (Agung, Alek, Dono, Jono) sengaja dibiarkan **tanpa transkrip**
karena file `.txt` aslinya berisi naskah penuh, sedangkan audionya hanya berisi 35
detik pertama. Transkrip yang tidak cocok justru merusak hasil kloning, jadi lebih
aman dibiarkan kosong — model punya ASR bawaan yang akan membaca sendiri audionya.

Kalau Anda mau menambahkan transkripnya, dengarkan audionya sampai habis, salin
persis kalimat yang benar-benar terucap, lalu tambahkan kolom `"transcript"` pada
blok suara itu di `voices.json`.

---

## Cara menambah suara

**1. Siapkan file audionya**

- Format `.wav` atau `.mp3`
- Panjang **5–15 detik**, paling bagus sekitar 10 detik
- Satu orang bicara saja, jelas, tanpa musik dan tanpa suara latar
- Hindari jeda panjang di awal atau akhir

**2. Unggah ke repo ini** lewat GitHub:
**Add file** → **Upload files** → seret file audionya → **Commit changes**.

**3. Daftarkan di `voices.json`**

Klik `voices.json` → ikon pensil ✏️ → tambahkan satu blok baru:

```json
{
  "id": "budi_narator",
  "name": "Budi — Narator",
  "language": "Indonesia",
  "gender": "Pria",
  "audio": "budi_narator.wav",
  "transcript": "Kalimat persis yang diucapkan di file audio."
}
```

Perhatikan tanda koma: setiap blok diakhiri koma **kecuali yang terakhir**.

**4. Muat ulang di Studio Engine**

Buka tool, klik tombol **Muat Ulang Suara** di bagian atas. Suara baru langsung
muncul di semua dropdown. Tidak perlu menjalankan ulang Colab.

## Arti setiap kolom

| Kolom | Wajib | Keterangan |
|---|---|---|
| `id` | ya | Nama unik, huruf kecil tanpa spasi |
| `name` | ya | Nama yang tampil di dropdown |
| `audio` | ya | Nama file di repo ini, atau URL lengkap |
| `language` | tidak | Ditampilkan di sebelah nama |
| `gender` | tidak | Sekadar catatan untuk Anda |
| `transcript` | tidak | **Sangat disarankan** — hasil kloning jauh lebih mirip |

## Kenapa transkrip penting

Tanpa transkrip, model harus menebak sendiri apa yang diucapkan di audio referensi.
Tebakan yang meleset membuat suara hasil terdengar aneh. Dengan transkrip yang persis,
hasilnya jauh lebih stabil dan mirip.

## Catatan hukum

Hanya masukkan suara yang Anda punya haknya, atau yang pemiliknya sudah memberi izin
tertulis. Meniru suara orang tanpa izin bisa melanggar hukum di banyak negara,
termasuk Indonesia.
