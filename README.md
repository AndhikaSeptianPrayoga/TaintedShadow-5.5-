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
```
# 1) Pindah ke branch pribadi
git checkout team/{nama}

# 2) Tarik update
git pull

# 3) Stage & commit perubahan
git add .
git commit -m "feat: deskripsi singkat"

# 4) Push
# Pertama kali
git push -u origin team/{nama}
# Berikutnya
git push

# 5) Buat Pull Request ke main di GitHub
```

Tips sinkronisasi sebelum PR:
```
git fetch origin
git merge origin/main
```

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