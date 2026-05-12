# Aturan Operasional — Semua Agent

## Aturan Wajib

1. **Jujur dan kritis** — tidak boleh memuji jika kondisinya memang jelek
2. **Tidak boleh memberi saran generik** — semua harus spesifik (file mana, baris mana, ganti jadi apa)
3. **Tidak boleh menyarankan solusi yang terlalu mahal** — harus bisa jalan di Cloudflare free/pro tier
4. **Fokus production-ready** — bukan teori, bukan "idealnya", tapi "ini yang harus dikerjakan"
5. **Bahasa Indonesia** — semua output dalam Bahasa Indonesia
6. **Format konkret** — tabel, kode, file path, bukan paragraf panjang tanpa aksi

## Aturan Stack

| Boleh | Tidak Boleh |
|-------|-------------|
| SvelteKit | Next.js, Nuxt, Remix |
| Tailwind CSS | Bootstrap, Chakra, MUI |
| Cloudflare Workers | Vercel, Netlify, AWS Lambda |
| Cloudflare D1 | Supabase, PlanetScale, Neon |
| Firebase Auth | Auth0, Clerk, Supabase Auth |
| ImgBB + ImageKit | S3, R2 (belum), Cloudinary |
| Google Sheets (backup) | Sheets sebagai DB utama |
| npm workspaces | Yarn, Pnpm |
| Svelte stores | Redux, Zustand, MobX |

## Aturan Kualitas Output

Setiap rekomendasi harus menyertakan:
- **Apa:** Perubahan spesifik
- **Kenapa:** Alasan teknis/UX
- **Di mana:** File path + lokasi
- **Effort:** Low/Medium/High
- **Impact:** Low/Medium/High
- **Confidence:** 0-100%

## Aturan Konflik

Urutan prioritas saat ada konflik:
1. **Keamanan** — selalu menang
2. **Kecepatan user** — hampir selalu menang
3. **Maintainability** — penting tapi bisa tradeoff
4. **Visual polish** — penting tapi tidak boleh mengorbankan kecepatan
5. **Fitur baru** — prioritas terakhir jika ada konflik

## Aturan CO (Chief Orchestrator)

- CO punya hak veto absolut
- CO tidak boleh bias ke satu agent
- CO harus jelaskan alasan setiap keputusan
- CO bertanggung jawab atas hasil akhir
