# TaintedShadow 5.5

Proyek Unreal Engine 5.5 untuk game/experience "The Tainted Shadow".

## Quick Setup
- Prasyarat: Git, Git LFS terpasang.
- Clone: `git clone https://github.com/AndhikaSeptianPrayoga/TaintedShadow-5.5-.git`
- Masuk folder: `cd TaintedShadow-5.5-`
- Aktifkan LFS: `git lfs install`
- Buka proyek: klik `The_TaintedShadow.uproject` di Unreal Engine 5.5.

## Struktur Branch
- `main`: branch utama (protected). Merge via Pull Request.
- `team/{nama}`: branch kerja per anggota.
  - Dibuat: `team/andhika`, `team/aris`, `team/nauf`, `team/raditya`, `team/radysena`, `team/irfan`.

## Tatacara Kirim Progress (Singkat)
Untuk anggota non-programmer, pakai langkah paling sederhana ini:
- Buka aplikasi GitHub Desktop
- Pilih `Repository` proyek ini
- Pilih `Current branch` → `team/{nama}`
- Klik `Fetch origin` lalu `Pull`
- Simpan perubahan Anda di Unreal (Save All)
- Di GitHub Desktop: isi `Summary` singkat → klik `Commit`
- Klik `Push origin`
- Klik `Create Pull Request` → target `main`

Tips sinkronisasi sebelum PR:
- Di GitHub Desktop: `Branch` → `Update from main`

## Panduan Lengkap
Lihat `TEAM_WORKFLOW.md` untuk detail alur, resolusi konflik, dan praktik terbaik aset Unreal.

## Git LFS
Aset besar (`.uasset`, `.umap`, `fbx`, gambar, audio, video) dilacak dengan Git LFS.
Apabila upload besar lambat atau sering putus, kurangi paralelisme:
```
git config --global lfs.concurrenttransfers 1
```

## Ignore
Folder hasil build/cache sudah dikecualikan di `.gitignore` (mis. `Saved/`, `Intermediate/`, `Binaries/`).