# AGENTS.md — Template Per-Project

> Copy file ini ke folder utama tiap project sebagai `AGENTS.md`. Isi bagian yang ada tanda `[ISI DI SINI]`. File ini dibaca Claude maupun Codex.
> Kalau proyeknya pakai Claude Code, bikin file `CLAUDE.md` isinya cuma 1 baris: `@AGENTS.md` — biar Claude baca file yang sama, ga perlu duplikat/nulis dua kali.
> **Jaga file ini di bawah ±150 baris.** Kalau kepanjangan, pecah jadi file di folder `.claude/rules/` per-topik — jangan numpuk semua di sini.

---

## Ringkasan Project

[ISI DI SINI — 1-2 kalimat: project ini buat apa, buat siapa]

## Stack & Command

[ISI DI SINI — teknologi yang dipakai, dan command yang beneran bisa langsung dijalanin, misal:]
- Install: `...`
- Jalanin dev server: `...`
- Test: `...`
- Build: `...`

## Branch

- **Branch kerja** (AI commit + push otomatis ke sini): [ISI DI SINI]
- **Branch live** (website asli — wajib izin Thisya): [ISI DI SINI, biasanya `master`/`main`]
- **Website report progres:** [ISI DI SINI — link]

## Struktur Folder Penting

[ISI DI SINI — folder utama dan isinya, 1 baris per folder, secukupnya aja]

---

## Alur Kerja Claude ↔ Codex (WAJIB, jangan diubah tanpa alasan kuat)

0. **Baca [`HANDOFF_CONTEXT.md`](HANDOFF_CONTEXT.md) dulu di awal SETIAP sesi baru** — jangan minta user jelasin ulang, jangan baca transkrip lama utuh.
0.5. **Kalau ada bagian HANDOFF_CONTEXT.md yang masih `[ISI]`/kosong** (terutama "lagi ngerjain apa", "rencana yang disepakati", "langkah selanjutnya") — **WAJIB berhenti dan tanya ke user dulu**: apa yang udah dibuat, rencana sebelumnya gimana, next-nya mau apa. JANGAN asumsi atau mulai kerja dari nol sebelum itu jelas.
1. **Rencana sesuai resiko** (aturan global 3.1): rendah → langsung; normal → rencana singkat; tinggi → rencana direview Codex dulu (maks 2 putaran).
2. **Claude ↔ Codex ngobrol langsung** lewat terminal (`codex exec` / `claude -p`), dicatat di log. Thisya bukan kurir.
3. **Ketergantungan luar belum tervalidasi** (library, API, browser) → tes kecil dulu sebelum bangun penuh.
4. **Sebelum lapor "selesai"** → bukti dicoba langsung, masuk website report (aturan global 3.2).
5. **Macet ~30 menit** → tanya Codex → masih macet: catat, lewatin, lanjut kerjaan lain (aturan global 3.5).
6. **Update HANDOFF_CONTEXT.md tiap checkpoint** (maks 1 layar).

## Changelog Project Ini

[ISI DI SINI — nama file changelog/progress log yang UDAH ADA di project ini (misal CHANGELOG.md, PROGRESS.md). Kalau belum ada, bikin 1x, jangan bikin baru-baru lagi tiap sesi.]

## Batasan / Permission

**Boleh otomatis tanpa nanya:**
- Baca file, jalanin test/lint, `git status`/`git diff`/`git log`
- Commit + push ke branch kerja (kode maupun dokumentasi)
[ISI DI SINI — tambahan spesifik project ini]

**Wajib nanya/nunggu approval dulu:**
- Push/merge ke branch live, deploy
- Migrasi ke database asli, hapus data, sentuh data asli (kandidat/karyawan)
- Nyentuh file di luar yang udah disebutin di rencana
- Menambahkan dependency/library baru
[ISI DI SINI — tambahan spesifik project ini]

---

## Definition of Done (checklist sebelum bilang "selesai")

- [ ] Udah dicoba jalan langsung (bukan cuma baca kode)?
- [ ] Kalau ada test baru, test itu beneran ngecek hasil yang benar (bukan cuma "ga error")?
- [ ] Ada bagian yang di-skip/gagal? Kalau ada, udah dilaporin jelas (bukan disembunyiin)?
- [ ] Laporan ke user pakai bahasa non-teknis (apa/kenapa/di mana/cara coba/hasil)?

---

## Zona yang Pernah Bermasalah (gotcha — tambahin tiap ada insiden baru)

> Diisi progresif. Tiap kali ada kesalahan yang makan waktu lama buat dibenerin, catet di sini biar ga kejadian lagi.

- [ISI DI SINI seiring berjalan — kosong dulu di awal project]
