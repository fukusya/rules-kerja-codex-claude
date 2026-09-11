# Cara Pasang Rules Ini ke Project Kamu

3 file yang udah disiapin:

| File | Ditaruh di | Fungsi |
|---|---|---|
| [`global/CLAUDE.md`](global/CLAUDE.md) | `~/.claude/CLAUDE.md` (folder home, 1x aja, berlaku ke SEMUA project) | Identitas kamu + gaya komunikasi + aturan lintas-project |
| [`project-template/AGENTS.md`](project-template/AGENTS.md) | `AGENTS.md` di folder utama tiap project (OKR, ATS, Siklus Kulit, Time Management, WhatsApp extension) | Alur kerja Claude↔Codex, permission, definition of done — diisi manual per-project |
| [`project-template/settings.example.json`](project-template/settings.example.json) | `.claude/settings.json` di tiap project | Yang beneran MAKSA (git push wajib nanya, dll) — bukan cuma tertulis |

## Langkah Pasang (1x setup)

### 1. Pasang yang global (sekali aja, berlaku semua project)

```bash
mkdir -p ~/.claude
cp global/CLAUDE.md ~/.claude/CLAUDE.md
```

### 2. Pasang ke tiap project (ulangi buat OKR, ATS, Siklus Kulit, Time Management, WhatsApp extension)

```bash
cp project-template/AGENTS.md /path/ke/project/AGENTS.md
mkdir -p /path/ke/project/.claude
cp project-template/settings.example.json /path/ke/project/.claude/settings.json
echo "@AGENTS.md" > /path/ke/project/CLAUDE.md
```

Terus **buka `AGENTS.md` di project itu, isi bagian `[ISI DI SINI]`** — stack, command, struktur folder, batasan spesifik project itu. Kalau project udah punya `CLAUDE.md` isinya banyak, jangan langsung timpa — gabungin dulu bagian yang masih relevan ke `AGENTS.md`, baru `CLAUDE.md`-nya diringkas jadi cuma `@AGENTS.md`.

## Kalau nanti ada koreksi baru

- Kalau kesalahannya **spesifik 1 project** → tambahin ke bagian "Zona yang Pernah Bermasalah" di `AGENTS.md` project itu.
- Kalau kesalahannya **bisa kejadian di project manapun** (soal gaya komunikasi, cara kerja Claude↔Codex, dll) → tambahin ke `global/CLAUDE.md` di repo ini, commit, push, terus copy ulang ke `~/.claude/CLAUDE.md`.
