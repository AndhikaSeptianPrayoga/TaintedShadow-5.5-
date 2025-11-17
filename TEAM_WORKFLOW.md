# Alur Kerja Tim TaintedShadow

Dokumen ini mendeskripsikan cara kerja tim untuk update progress harian dan proses merge oleh leader.

## Struktur Branch
- `main`: branch utama, dilindungi. Semua perubahan masuk via Pull Request (PR).
- `team/{nama}`: branch kerja masing-masing anggota.
  - Dibuat untuk: `team/andhika`, `team/aris`, `team/nauf`, `team/raditya`, `team/radysena`, `team/irfan`.

## Persiapan Anggota
- Clone repo: `git clone https://github.com/AndhikaSeptianPrayoga/TaintedShadow-5.5-.git`
- Masuk folder: `cd TaintedShadow-5.5-`
- Aktifkan Git LFS: `git lfs install`
- Checkout branch pribadi: `git checkout team/{nama}`

## Alur Upload Progress
- Sinkronisasi awal: `git pull`
- Lakukan perubahan di Unreal, pastikan folder yang dikecualikan tidak ikut ter-commit (`Saved/`, `Intermediate/`, dll sesuai `.gitignore`).
- Stage perubahan: `git add .`
- Commit dengan pesan jelas:
  - Contoh: `git commit -m "feat(level): tambah layout ruang latihan"`
  - Gunakan kata kunci umum: `feat`, `fix`, `refactor`, `content`, `chore`.
- Push ke branch pribadi: `git push -u origin team/{nama}`
- Buat Pull Request ke `main` di GitHub dengan template deskripsi:
  - Ringkasan perubahan
  - Dampak ke konten/asset lain
  - Cara uji (langkah untuk verifikasi di editor)
  - Checklist: build/test manual di Unreal, bebas konflik

## Resolusi Konflik
- Jika PR konflik dengan `main`:
  - `git checkout team/{nama}`
  - `git fetch origin` dan `git merge origin/main`
  - Selesaikan konflik di file terkait, uji ulang di Unreal
  - `git add .` lalu `git commit` dan `git push`
  - Update PR sampai status konflik hilang

## Review & Merge oleh Leader
- Tinjau diff PR, fokus pada file `.uasset/.umap` yang terubah serta perubahan `.ini` di `Config/`.
- Pastikan:
  - Tidak ada file cache/temporary (`Saved/`, `Intermediate/`) di PR
  - Aset besar ter-track oleh LFS (`.gitattributes` sudah mencakup tipe file)
  - Build/preview di Unreal tidak error
- Pilihan merge:
  - Disarankan `Squash and merge` untuk merapikan sejarah commit per fitur
  - Gunakan `Merge commit` jika ingin mempertahankan urutan beberapa commit
- Setelah merge:
  - Hapus branch PR di remote jika sudah tidak diperlukan
  - Buat tag release bila perlu: `git tag v0.1.0 && git push origin v0.1.0`

## Praktik Terbaik Aset Besar
- Hindari commit folder hasil build: `Binaries/`, `Saved/`, `Intermediate/`.
- Tambahkan tipe aset baru ke `.gitattributes` bila diperlukan (misal `*.tif`, `*.psd`).
- Untuk upload besar yang lambat, kurangi paralelisme LFS:
  - `git config --global lfs.concurrenttransfers 1`

## Naming & Konvensi
- Nama branch: `team/{nama}` huruf kecil, tanpa spasi.
- Pesan commit singkat, deskriptif, pakai kata kunci.
- PR judul: `[Nama] - Ringkas perubahan`, contoh: `[Raditya] - Update AI patrol di level desa`.

## Checklist Sebelum PR
- [ ] Unreal bisa dibuka tanpa error
- [ ] Tidak ada file dari folder yang di-ignore
- [ ] Perubahan diuji di level terkait
- [ ] Deskripsi PR lengkap