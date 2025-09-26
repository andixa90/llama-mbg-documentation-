# Integrasi OpenRouter API untuk Pawon AI

## Ringkasan Perubahan

Aplikasi Pawon AI telah berhasil diintegrasikan dengan OpenRouter API sebagai alternatif dari Gemini API. Berikut adalah perubahan yang telah dilakukan:

### 1. File Baru yang Dibuat

#### `src/openrouter.js`
- Handler khusus untuk OpenRouter API
- Menggunakan model GPT-4 (dapat diubah sesuai kebutuhan)
- Mendukung CORS untuk akses dari frontend
- Validasi response dan error handling yang robust

### 2. File yang Dimodifikasi

#### `src/index.js`
- Menambahkan routing untuk endpoint `/functions/openrouter`
- Mendukung method POST dan OPTIONS (untuk CORS)

#### `public/pawon-ai.html`
- Mengganti fungsi `callGeminiAPI` menjadi `callOpenRouterAPI`
- Mengupdate endpoint dari `/functions/gemini` ke `/functions/openrouter`
- Menghapus parameter `generationConfig` yang spesifik untuk Gemini

## Setup untuk Deployment

### 1. Environment Variables

Karena repository private, Anda dapat menyimpan API key langsung di `wrangler.toml`:

#### Edit file `wrangler.toml`:
```toml
[vars]
GEMINI_API_KEY = "AIzaSyAvyE_q2lGEWyQNQQpOtq4-p4nb6Td4NO0"
OPENROUTER_API_KEY = "your_openrouter_api_key_here"
```

**Catatan**: Karena repo private, menyimpan di `vars` aman dilakukan. Untuk repo public, gunakan `wrangler secret put`.

### 2. Mendapatkan API Key OpenRouter

1. Daftar di [OpenRouter.ai](https://openrouter.ai/)
2. Masuk ke dashboard dan buat API key baru
3. Copy API key tersebut untuk digunakan sebagai environment variable

### 3. Model yang Tersedia

File `openrouter.js` saat ini menggunakan model `gpt-4`. Anda dapat menggantinya dengan model lain yang tersedia di OpenRouter:

- `gpt-4-turbo`
- `gpt-3.5-turbo`
- `claude-3-sonnet`
- `claude-3-haiku`
- `meta-llama/llama-3-8b-instruct`
- Dan banyak model lainnya

Untuk mengganti model, edit file `src/openrouter.js` pada baris:
```javascript
model: "gpt-4", // Ganti dengan model yang diinginkan
```

### 4. Testing

Untuk menguji implementasi:

1. Deploy aplikasi ke Cloudflare Pages/Workers
2. Pastikan environment variable `OPENROUTER_API_KEY` sudah diset
3. Buka halaman `pawon-ai.html`
4. Pilih pulau, provinsi, dan kelompok sasaran
5. Klik tombol "Buat Rekomendasi Menu"
6. Sistem akan menggunakan OpenRouter API untuk menghasilkan menu

### 5. Error Handling

Aplikasi sudah dilengkapi dengan error handling yang baik:
- Validasi API key
- Validasi response dari OpenRouter
- Error message yang informatif untuk user
- Fallback handling untuk berbagai skenario error

### 6. Keamanan

API key OpenRouter disimpan dengan aman sebagai environment variable di server dan tidak pernah terekspos ke client-side code.

## Biaya dan Limit

OpenRouter memiliki struktur pricing yang berbeda untuk setiap model. Pastikan untuk:
1. Cek pricing di dashboard OpenRouter
2. Set limit penggunaan jika diperlukan
3. Monitor usage secara berkala

## Troubleshooting

### Jika API tidak berfungsi:
1. Pastikan environment variable `OPENROUTER_API_KEY` sudah diset dengan benar
2. Cek di browser console untuk error messages
3. Pastikan model yang dipilih tersedia di OpenRouter
4. Cek balance/credit di dashboard OpenRouter

### Jika response tidak sesuai format:
- Model OpenRouter mungkin menghasilkan format response yang sedikit berbeda
- Adjust prompt atau model yang digunakan jika diperlukan