# Menjalankan Subnetlist di GitHub Codespaces

Panduan ini menjelaskan cara menjalankan aplikasi Next.js Subnetlist di Codespaces.

## Membuat Codespace

1. Buka repository [FahmiHusaini0/subnetlist](https://github.com/FahmiHusaini0/subnetlist).
2. Pilih **Code → Codespaces → Create codespace on master**.
3. Tunggu hingga dev container selesai dibuat. Konfigurasi akan memasang dependensi dengan `npm ci` dan menyiapkan `.env` dari `.env.example` jika file lokal tersebut belum ada.

Jika Codespace sudah terbuka sebelum konfigurasi devcontainer diperbarui, jalankan **Codespaces: Rebuild Container** dari Command Palette (`Ctrl+Shift+P` / `Cmd+Shift+P`).

## Menjalankan aplikasi

Di terminal Codespace, jalankan:

```bash
npm run dev
```

Saat diminta, buka port **3000** melalui tab **Ports**. Port ini dikonfigurasi sebagai **Private**; jangan ubah menjadi Public kecuali memang diperlukan dan Anda memahami risikonya.

## Variabel lingkungan

`.env.example` adalah template, sedangkan `.env` bersifat lokal dan diabaikan Git. Isi nilai yang diperlukan hanya di `.env` atau melalui Codespaces Secrets. Jangan masukkan token, private key, kata sandi, atau secret lain ke `.env.example`, source code, atau commit.

Jika mengubah `.env.example`, ingat bahwa Codespaces hanya menyalinnya saat `.env` belum ada. Perbarui `.env` lokal secara manual bila diperlukan, tanpa menimpa nilai lokal yang sudah ada.

## Perintah berguna

```bash
npm ci          # pasang dependensi sesuai package-lock.json
npm run dev     # jalankan server development
npm run build   # uji build produksi
```

Jika ada perubahan dependensi, perbarui lockfile dengan npm dan commit bersama perubahan `package.json` agar `npm ci` tetap bekerja.

## Keamanan

- Gunakan hanya port yang diperlukan; port aplikasi 3000 disetel private.
- Jangan menjalankan perintah atau skrip dari sumber yang tidak dipercaya di Codespace.
- Jangan simpan secret di repository. Jika secret terlanjur ter-commit, hapus dari repo dan segera rotasi/ganti secret tersebut; menghapus file di commit terbaru saja tidak menghapusnya dari riwayat Git.
- Devcontainer adalah lingkungan pengembangan, bukan konfigurasi deployment produksi.
