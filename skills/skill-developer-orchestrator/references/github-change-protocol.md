# GitHub Change Protocol

Berlaku hanya jika konektor GitHub atau akses repository tersedia dan diotorisasi. URL bukan kredensial dan tidak membuktikan write permission.

## A. Readiness and identity
1. Normalisasi URL menjadi owner/repository; pastikan tidak ambigu.
2. Baca metadata, visibility, archived state, default branch, akses dan aturan kontribusi.
3. Catat base branch HEAD SHA dan waktu pemeriksaan.
4. Inventarisasi source-of-truth, docs, tests, workflows, konfigurasi.
5. Periksa branch/PR yang sudah ada untuk menghindari duplikasi.
6. Read access tidak membuktikan write access.

## B. Safe branch strategy
- Buat branch bernama jelas dari SHA yang baru diverifikasi, misalnya sdo/<scope>-YYYYMMDD.
- Jangan menulis ke default branch secara langsung.
- Jika base head berubah, baca ulang dan rekonsiliasi; jangan menerapkan patch lama secara buta.

## C. Patch application
1. Buat manifest ADD/UPDATE/DELETE: path, baseline SHA, alasan, requirement, test.
2. Simpan konteks dan blob SHA sebelum update.
3. Untuk multi-file atomic commit gunakan Git data API hanya bila tree/base SHA tersedia dan kontrak tool dipahami. Jika tidak, lakukan contents API berurutan dan catat tiap commit.
4. Update harus memakai blob SHA terkini; file baru harus dipastikan belum ada.
5. Jangan menghapus file tanpa alasan, bukti dependency, dan otorisasi.
6. Fetch ulang file setelah write dan verifikasi branch head/commit SHA.

## D. Validation and PR
1. Review seluruh diff.
2. Jalankan tes yang tersedia dan aman; catat PASS/FAIL/BLOCKED/NOT_RUN.
3. CI hanya dapat diklaim dari status commit tepat yang diperiksa.
4. Buat PR yang menjelaskan problem, scope, changes, evidence, tests, limits, rollback. Gunakan draft bila validasi belum lengkap.
5. Read back PR number, state, draft, base/head, SHA, checks, reviews, URL.
6. Jangan merge/release tanpa persetujuan terpisah.

## E. Recovery
- Bila expected SHA ditolak, baca ulang head; jangan force update.
- Rekonsiliasi perubahan concurrent.
- Pada partial write, catat commit/file yang berhasil dan gagal; jangan ulangi membabi buta.
- Permission denied berarti berhenti, bukan mencari jalan pintas.
- Rollback harus punya baseline dan izin; jangan force-push.

## F. Completion evidence
Laporkan repository, base branch/SHA, work branch, file changes, commit SHA, PR URL/state/draft/base/head, checks, reviews, test yang belum berjalan, dan apakah perubahan hanya di branch, merged, atau released. PR_OPEN bukan MERGED; MERGED bukan RELEASED.
